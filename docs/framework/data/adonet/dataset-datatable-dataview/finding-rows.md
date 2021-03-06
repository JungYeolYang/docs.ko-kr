---
title: 행 찾기
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: e5a48c5caf9239e0e7b7f2e7a3ad8ab5df168ba1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684192"
---
# <a name="finding-rows"></a>행 찾기
<xref:System.Data.DataView.Find%2A>의 <xref:System.Data.DataView.FindRows%2A> 및 <xref:System.Data.DataView> 메서드를 사용하여 행의 정렬 키 값에 따라 행을 검색할 수 있습니다. 검색의 대/소문자 구분 값을 **찾을** 및 **FindRows** 메서드에 의해 결정 됩니다는 **CaseSensitive** 속성에 <xref:System.Data.DataTable>합니다. 검색 값이 기존 정렬 키 값 전체와 일치해야 결과를 반환할 수 있습니다.  
  
 합니다 **찾을** 의 인덱스를 사용 하 여 정수를 반환 하는 메서드는 <xref:System.Data.DataRowView> 검색 조건과 일치 하는 합니다. 둘 이상의 행 일치 조건과 일치 하는 첫 번째 인덱스만 **DataRowView** 반환 됩니다. 일치 하는 경우 **찾을** -1을 반환 합니다.  
  
 여러 행과 일치 하는 검색 결과 반환 하려면 사용 합니다 **FindRows** 메서드. **FindRows** 처럼 작동 합니다 **찾을** 메서드를 반환 한다는 점을 제외 하 고를 **DataRowView** 에서 일치 하는 모든 행을 참조 하는 배열을 **DataView**. 일치 하는 경우는 **DataRowView** 배열은 비어 있게 됩니다.  
  
 사용 하는 **찾을** 또는 **FindRows** 정렬을 지정 해야 하는 방법을 설정 하거나 주문 **ApplyDefaultSort** 에 **true** 또는 사용 하 여는 **정렬** 속성입니다. 정렬 순서를 지정하지 않으면 예외가 throw됩니다.  
  
 **찾을** 하 고 **FindRows** 메서드는 값의 배열 길이가 정렬 순서에서 열 수와 일치 하는 입력으로 사용 합니다. 하나의 열에 대해 정렬하는 경우에는 하나의 값을 전달할 수 있습니다. 정렬 순서에 여러 열이 포함된 경우에는 개체 배열을 전달합니다. 여러 열 정렬에 대 한 개체 배열의 값 일치 해야 합니다에 지정 된 열의 순서를 **정렬** 의 속성을 **DataView**합니다.  
  
 다음 코드 예제는 **찾을** 메서드를 호출 하는 **DataView** 단일 열 정렬 순서를 사용 하 여 합니다.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 경우에 **정렬** 여러 열을 지정 하는 속성, 지정 된 순서에서 각 열에 대 한 검색 값을 사용 하 여 개체 배열을 전달 해야 합니다는 **정렬** 속성을 다음 코드 예제와 같이 합니다.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>참고자료
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET 관리되는 공급자 및 데이터 집합 개발자 센터](https://go.microsoft.com/fwlink/?LinkId=217917)
