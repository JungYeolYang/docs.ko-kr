---
title: PredictionEngine을 사용하여 한 번에 하나씩 예측 수행 - ML.NET
description: ML.NET PredictionEngine을 사용하여 한 번에 하나씩 예측을 수행하는 방법 알아보기
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 328067816be37c9490ae71974e3f6da4ae079f25
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092035"
---
# <a name="use-the-predictionengine-to-make-one-prediction-at-a-time---mlnet"></a>PredictionEngine을 사용하여 한 번에 하나씩 예측 수행 - ML.NET 

모든 ML.NET 모델은 변환기이므로 `model.Transform`을 사용해서 `DataView`에 모델을 적용하여 예측을 수행합니다. 

그러나 예측할 ‘데이터 세트’가 없고 한 번에 하나씩 예제를 받는 경우가 보다 일반적입니다. 예를 들어 ASP.NET 웹 사이트의 일부로 모델을 실행하며, 들어오는 HTTP 요청에 대해 예측을 수행해야 합니다.

`PredictionEngine`은 예측 파이프라인을 통해 한 번에 하나씩 예제를 실행합니다.

다음은 미리 빌드된 아이리스 예측 데이터 세트 모델을 사용하는 전체 예제입니다.

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("SepalLength",DataKind.R4,0),
        new TextLoader.Column("SepalWidth",DataKind.R4,1),
        new TextLoader.Column("PetalLength",DataKind.R4,2),
        new TextLoader.Column("PetalWidth",DataKind.R4,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    separatorChar: ',',
    hasHeader: true
);

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("Data", "PredictedLabel")));

// Train the model.
var model = pipeline.Fit(trainData);
```

[스키마 이해](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md)를 예측에 사용하려면 다음과 같은 클래스 쌍을 정의합니다.

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

이제 예측 코드는 다음과 같습니다.

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction engine, instead of
// creating one per prediction.
var predictionEngine = model.CreatePredictionEngine<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionEngine.
var prediction = predictionEngine.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```
