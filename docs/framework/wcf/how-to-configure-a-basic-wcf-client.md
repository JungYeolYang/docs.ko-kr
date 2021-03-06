---
title: '방법: 기본 Windows Communication Foundation 클라이언트를 구성 합니다.'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 18acec48b2af78877f99335da38ccb0ae8942824
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332323"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>방법: 기본 Windows Communication Foundation 클라이언트를 구성 합니다.

기본 Windows Communication Foundation (WCF) 응용 프로그램을 만드는 데 필요한 6 가지 작업 중 다섯 번째입니다. 6가지 모든 작업에 대한 개요는 [초보자를 위한 자습서](../../../docs/framework/wcf/getting-started-tutorial.md) 항목을 참조하세요.

이 항목에서는 사용 하 여 생성 된 클라이언트 구성 파일에 설명 합니다 **서비스 참조 추가** Visual Studio의 기능 또는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)합니다. 클라이언트를 구성하려면 클라이언트에서 서비스에 액세스하는 데 사용하는 엔드포인트를 지정해야 합니다. 끝점 주소, 바인딩 및 계약에 있고 이러한 각 클라이언트를 구성 하는 동안 지정 해야 합니다.

## <a name="configure-a-windows-communication-foundation-client"></a>Windows Communication Foundation 클라이언트 구성

GettingStartedClient 프로젝트에서 생성된 구성 파일(App.config)을 엽니다. 다음 예제에서는 생성된 구성 파일을 보여 줍니다. 아래는 [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 섹션에서 찾을 합니다 [ \<끝점 >](../configure-apps/file-schema/wcf/endpoint-element.md) 요소입니다.

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
          <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

이 예제에서는 다음 주소에 위치한 서비스에 액세스 하는 클라이언트 끝점 구성: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`합니다.

엔드포인트 요소는 WCF 클라이언트와 서비스 사이의 통신에 `ServiceReference1.ICalculator` 서비스 계약을 사용하도록 지정합니다. WCF 채널은 시스템에서 제공한 <xref:System.ServiceModel.WSHttpBinding>을 사용하여 구성합니다. 사용 하 여 생성 된이 계약은 **서비스 참조 추가** Visual Studio에서. 실질적으로 GettingStartedLib 프로젝트에 정의된 계약의 사본입니다. 
  <xref:System.ServiceModel.WSHttpBinding> 바인딩은 HTTP를 전송, 상호 운용 가능한 보안 및 기타 구성 세부 사항으로 지정합니다.

이 구성을 사용 하 여 생성된 된 클라이언트를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 클라이언트를 사용 하 여](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)입니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [방법: WCF 클라이언트를 사용 합니다.](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a>참고자료

- [바인딩을 사용하여 서비스 및 클라이언트 구성](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [ServiceModel Metadata 유틸리티 도구(Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [방법: 클라이언트 만들기](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [시작](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [자체 호스팅](../../../docs/framework/wcf/samples/self-host.md)