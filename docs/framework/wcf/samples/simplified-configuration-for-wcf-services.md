---
title: WCF 서비스를 위한 단순화된 구성
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: c0d5f46e6ace71ad4732f8d387b3289b1d4105e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516371"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF 서비스를 위한 단순화된 구성
이 샘플에 구현 하 여 일반적인 서비스 및 Windows Communication Foundation (WCF)를 사용 하 여 클라이언트를 구성 하는 방법을 보여 줍니다. 이 샘플은 다른 모든 기본 기술 샘플의 기준이 됩니다.  
  
 서비스와 통신하기 위한 엔드포인트를 노출하는 이 서비스에서는 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]의 단순화된 구성을 사용합니다. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 이전 버전에서 엔드포인트는 일반적으로 구성 파일(Web.config)에서 다음 예제 구성 코드와 같이 정의됩니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]에서는 `<service>`가 선택적 요소입니다. 서비스에서 엔드포인트를 정의하지 않을 경우 각 기본 주소의 엔드포인트와 구현된 계약이 서비스에 추가됩니다. 기본 주소가 계약 이름에 추가되어 엔드포인트가 결정되고 바인딩은 주소 스키마에 의해 결정됩니다. 다음 코드 예제에서는 단순화된 구성 파일을 보여 줍니다. 서비스에서 액세스할 수 있습니다 구성 된 대로 `http://localhost/servicemodelsamples/service.svc` 동일한 컴퓨터에 클라이언트에서. 원격 컴퓨터의 클라이언트가 서비스에 액세스하려면 localhost 대신 정규화된 도메인 이름을 지정해야 합니다. 기본적으로 서비스에서는 메타데이터를 노출하지 않습니다. 따라서 서비스에서는 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 동작을 설정합니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>이 샘플을 사용하려면  
  
1.  수행 했는지 확인 합니다 [Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)합니다.  
  
2.  지침에 따라 솔루션을 빌드하려면 [Building Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)합니다.  
  
3.  다음 단계에 따라 샘플을 실행합니다.  
  
    1.  마우스 오른쪽 단추로 클릭 합니다 **서비스** 프로젝트를 마우스 **시작 프로젝트로 설정**을 누릅니다 **ctrl+f5**합니다.  
  
    2.  서비스가 실행 중이라는 콘솔 출력이 나타날 때까지 기다립니다.  
  
    3.  마우스 오른쪽 단추로 클릭 합니다 **클라이언트** 프로젝트를 마우스 **시작 프로젝트로 설정**을 누릅니다 **ctrl+f5**합니다.  
  
> [!IMPORTANT]
>  컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  이 디렉터리가 없으면로 이동 [Windows Communication Foundation (WCF) 및.NET Framework 4 용 Windows WF (Workflow Foundation) 샘플](https://go.microsoft.com/fwlink/?LinkId=150780) 모든 Windows Communication Foundation (WCF)를 다운로드 하 고 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플. 이 샘플은 다음 디렉터리에 있습니다.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>참고자료
- [AppFabric 관리 샘플](https://go.microsoft.com/fwlink/?LinkId=193960)
- [단순화된 구성](../../../../docs/framework/wcf/simplified-configuration.md)
