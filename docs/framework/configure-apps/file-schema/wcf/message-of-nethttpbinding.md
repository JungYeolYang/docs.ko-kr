---
title: <message>의 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 66e854ca9dd33b608b93dae08376caaf590bd97f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277136"
---
# <a name="message-of-nethttpbinding"></a>\<메시지 >의 \<netHttpBinding >
메시지 수준 보안 설정을 정의 합니다 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)합니다.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netHttpBinding>  
\<binding>  
\<security>  
\<message>  
  
## <a name="syntax"></a>구문  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|algorithmSuite|메시지 암호화 및 키 래핑 알고리즘을 설정합니다. 이 특성은 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 형식이며 알고리즘 및 키 크기를 지정합니다. 이러한 알고리즘은 WS-SecurityPolicy(Security Policy Language) 사양에 지정된 알고리즘에 매핑됩니다.<br /><br /> 기본값은 `Basic256`입니다.|  
|clientCredentialType|메시지 기반 보안을 사용하여 클라이언트 인증을 수행할 때 사용되는 자격 증명의 형식을 지정합니다. 기본값은 `UserName`입니다.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 특성  
  
|값|설명|  
|-----------|-----------------|  
|UserName|-UserName 자격 증명을 사용 하 여 서버에 클라이언트 인증에 필요 합니다. 이 자격 증명은 <`clientCredentials`> 요소를 사용하여 지정해야 합니다.<br />WCF에서는 암호 다이제스트를 보내거나 암호를 사용 하 고 메시지 보안에 이러한 키를 사용 하 여 키를 파생 없습니다. 따라서 WCF 사용자 이름 자격 증명을 사용 하는 경우 전송에 보안을 적용 합니다. `basicHttpBinding`의 경우 SSL 채널을 설정해야 합니다.|  
|인증서|클라이언트가 인증서를 사용하여 서버의 인증을 받도록 요구합니다. 이 경우 <`clientCredentials`> 및 <`clientCertificate`>를 사용하여 클라이언트 자격 증명을 지정해야 합니다. 또한 메시지 보안 모드를 사용하는 경우 서비스 인증서를 사용하여 클라이언트를 구축해야 합니다. 서비스 자격 증명은이 예에서 사용 하 여 지정 해야 합니다 <xref:System.ServiceModel.Description.ClientCredentials> 클래스 또는 `ClientCredentials` 동작 요소 및 서비스를 지정 합니다. 인증서를 사용 하는 \<serviceCertificate > serviceCredentials 요소입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|<`security`> 요소의 <`netHttpBinding`>|<`netHttpBinding`> 요소의 보안 기능을 정의합니다.|  
  
## <a name="example"></a>예제  
 이 샘플에서는 basicHttpBinding 및 메시지 보안을 사용하는 응용 프로그램을 구현하는 방법을 보여 줍니다. 다음 서비스 구성 예제에서 끝점 정의는 basicHttpBinding을 지정하고 `Binding1`이라는 바인딩 구성을 참조합니다. 서비스가 클라이언트에게 자신을 인증하는 데 사용하는 인증서는 구성 파일의 `behaviors` 섹션에 있는 `serviceCredentials` 요소 아래에 설정됩니다. 클라이언트가 서비스에 자신을 인증하는 데 사용하는 인증서에 적용되는 유효성 검사 모드 또한 `behaviors` 섹션에서 `clientCertificate` 요소 아래에 설정됩니다.  
  
 동일한 바인딩 및 보안 세부 정보가 클라이언트 구성 파일에 지정됩니다.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>참고자료
- [서비스 및 클라이언트에 보안 설정](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [바인딩](../../../../../docs/framework/wcf/bindings.md)
- [시스템 제공 바인딩 구성](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [바인딩을 사용하여 서비스 및 클라이언트 구성](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
