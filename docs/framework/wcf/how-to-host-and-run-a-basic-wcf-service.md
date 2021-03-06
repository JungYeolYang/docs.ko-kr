---
title: 호스트 및 기본 Windows Communication Foundation 서비스를 실행 하는 방법
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 73633c2c6119204f2fb608b32ae794a2e07b27d0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747076"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>호스트 및 기본 Windows Communication Foundation 서비스를 실행 하는 방법

WCF(Windows Communication Foundation) 애플리케이션을 만드는 데 필요한 6가지 작업 중 세 번째 작업입니다. 6가지 모든 작업에 대한 개요는 [초보자를 위한 자습서](getting-started-tutorial.md) 항목을 참조하세요.

이 항목에서는 콘솔 애플리케이션에서 WCF(Windows Communication Foundation) 서비스를 호스팅하는 방법에 대해 설명합니다. 이 절차는 다음 단계로 구성됩니다.

- 서비스를 호스팅할 콘솔 응용 프로그램 프로젝트를 만듭니다.

- 서비스에 대한 서비스 호스트를 만듭니다.

- 메타데이터 교환을 사용하도록 설정합니다.

- 서비스 호스트를 엽니다.

이 작업에서 작성된 전체 코드 목록은 이 절차 다음에 나오는 다음 예제에 제공되어 있습니다.

## <a name="create-a-new-console-application-to-host-the-service"></a>서비스를 호스팅할 새 콘솔 응용 프로그램 만들기

1. Getting Started 솔루션을 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 Visual Studio에서 새 콘솔 응용 프로그램 프로젝트를 만듭니다 **추가** > **새 프로젝트**합니다. 에 **새 프로젝트 추가** 대화 상자의 왼쪽에 있는 선택에서 **Windows Desktop** 에서 범주 **Visual C#** 또는 **Visual Basic**합니다. 선택 된 **콘솔 앱 (.NET Framework)** 템플릿을 선택한 후 프로젝트 이름을 **GettingStartedHost**합니다.

2. GettingStartedLib 프로젝트에 대 한 참조를 GettingStartedHost 프로젝트에 추가 합니다. 마우스 오른쪽 단추로 클릭 합니다 **참조** GettingStartedHost 프로젝트의 폴더 **솔루션 탐색기**를 선택한 후 **참조 추가**합니다. 에 **참조 추가** 대화 상자에서 **솔루션** 대화 상자의 왼쪽에서 대화 상자 가운데에서 GettingStartedLib를 선택 하 고 선택한 **추가**합니다. 이제 GettingStartedLib에 정의된 형식을 GettingStartedHost 프로젝트에서 사용할 수 있습니다.

3. System.ServiceModel에 대 한 참조를 GettingStartedHost 프로젝트에 추가 합니다. 마우스 오른쪽 단추로 클릭 합니다 **참조** GettingStartedHost 프로젝트의 폴더 **솔루션 탐색기** 선택한 **참조 추가**합니다. 에 **참조 추가** 대화 상자에서 **프레임 워크** 대화 상자의 왼쪽에서 **어셈블리**합니다. 찾기 및 선택 **System.ServiceModel**를 선택한 후 **확인**합니다. 선택 하 여 솔루션을 저장할 **파일** > **모두 저장**합니다.

## <a name="host-the-service"></a>서비스 호스트

편집할 Program.cs 또는 Module.vb 파일을 열고 다음 코드를 입력합니다.

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**1 단계** -서비스의 기본 주소를 보유할 Uri 클래스의 인스턴스를 만듭니다. 서비스는 기본 주소와 선택적 URI를 포함하는 URL로 식별됩니다. 기본 주소 형식은 다음과 같습니다. [전송]://[시스템 이름 또는 도메인][:선택적 포트 번호]/[선택적 URI 세그먼트]계산기 서비스의 기본 주소는 HTTP 전송, 로컬 호스트, 포트 8000 및 URI 세그먼트 “GettingStarted”를 사용합니다.

**2 단계** –의 인스턴스를 만듭니다는 <xref:System.ServiceModel.ServiceHost> 서비스를 호스트 하는 클래스입니다. 생성자는 서비스 계약을 구현하는 클래스 형식과 서비스의 기본 주소, 두 가지 매개 변수를 사용합니다.

**3 단계** – 만듭니다는 <xref:System.ServiceModel.Description.ServiceEndpoint> 인스턴스. 서비스 엔드포인트는 주소, 바인딩 및 서비스 계약으로 구성되어 있습니다. 따라서 <xref:System.ServiceModel.Description.ServiceEndpoint> 생성자는 서비스 계약 인터페이스 형식, 바인딩 및 주소를 사용합니다. 서비스 계약은 사용자가 정의한 `ICalculator`이며 서비스 형식에 구현합니다. 이 예제에 사용된 바인딩은 WS-* 사양을 따르는 엔드포인트에 연결하는 데 사용되는 기본 바인딩인 <xref:System.ServiceModel.WSHttpBinding>입니다. WCF 바인딩에 대한 자세한 내용은 [WCF 바인딩 개요](bindings-overview.md)를 참조하세요. 엔드포인트를 식별하기 위해 주소가 기본 주소에 추가됩니다. 끝점에 대 한 정규화 된 주소 이므로이 코드에서 지정 된 주소는 "CalculatorService" `"http://localhost:8000/GettingStarted/CalculatorService"`합니다.

> [!IMPORTANT]
> .NET Framework 4 이상을 사용할 때 서비스 엔드포인트 추가는 선택 사항입니다. 이러한 버전에서 코드 또는 구성에 엔드포인트가 추가되지 않으면 WCF가 기본 주소의 각 결합에 기본 엔드포인트 하나씩을 추가하고 서비스에서 구현한 계약을 추가합니다. 기본 엔드포인트에 대한 자세한 내용은 [엔드포인트 주소 지정](specifying-an-endpoint-address.md)을 참조하세요. 기본 엔드포인트, 바인딩 및 동작에 대한 자세한 내용은 [단순화된 구성](simplified-configuration.md) 및 [WCF 서비스를 위한 단순화된 구성](./samples/simplified-configuration-for-wcf-services.md)을 참조하세요.

**4 단계** – 메타 데이터 교환을 사용 하도록 설정 합니다. 클라이언트는 메타데이터 교환을 사용하여 서비스 작업을 호출하는 데 사용되는 프록시를 생성합니다. 메타데이터 교환을 활성화하려면 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 인스턴스를 만들고 해당 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 속성을 `true`로 설정한 다음 동작을 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 인스턴스의 <xref:System.ServiceModel.ServiceHost> 컬렉션에 추가합니다.

**5 단계** Open –는 <xref:System.ServiceModel.ServiceHost> 들어오는 메시지를 수신 대기 합니다. 코드는 사용자가 Enter를 누를 때까지 기다립니다. 이를 수행하지 않으면 응용 프로그램이 즉시 닫히고 서비스가 종료합니다. 또한 사용된 try/catch 블록도 주의하십시오. <xref:System.ServiceModel.ServiceHost>를 인스턴스화한 후에는 나머지 코드가 try/catch 블록에 배치됩니다. 안전 하 게에서 throw 된 예외를 catch 하는 방법에 대 한 자세한 내용은 <xref:System.ServiceModel.ServiceHost>를 참조 하세요 [사용 하 여 닫기 및 중단 WCF 클라이언트 리소스를 해제 하려면](samples/use-close-abort-release-wcf-client-resources.md)

> [!IMPORTANT]
> WCF 서비스 라이브러리에 추가 하면 Visual Studio 호스트할 수 있습니다에 대 한 서비스 호스트를 시작 하 여 디버그 하는 경우. 충돌을 피하기 위해이 비활성화할 수 있습니다. 
> 1. GettingStartedLib에 대 한 프로젝트 속성을 엽니다.
> 2. 로 이동 **WCF 옵션** 의 선택을 취소 **WCF 서비스 호스트 시작 디버깅할 때**합니다.

## <a name="verify-the-service-is-working"></a>서비스가 작동 확인

1. GettingStartedHost 콘솔 실행 Visual Studio 내부에서 응용 프로그램입니다.

   서비스는 관리자 권한으로 실행 되어야 합니다. 관리자 권한으로 Visual Studio를 열었으므로 GettingStartedHost도 관리자 권한으로 실행 됩니다. 사용 하 여 새 명령 프롬프트를 열 수도 있습니다 **관리자 권한으로 실행** 내에서 service.exe를 실행 합니다.

2. 웹 브라우저를 열고 서비스의 디버그 페이지인 `http://localhost:8000/GettingStarted/`합니다. **참고! 슬래시를 종료 하는 중요 합니다.**

## <a name="example"></a>예제

다음 예제에는 자습서의 이전 단계의 서비스 계약과 구현이 포함되어 있으며 콘솔 응용 프로그램에서 서비스를 호스팅합니다.

이 명령줄 컴파일러로 컴파일하려면 IService1.cs 및 컴파일합니다 Service1.cs 참조 하는 클래스 라이브러리로 `System.ServiceModel.dll`합니다. Program.cs를 콘솔 응용 프로그램으로 컴파일하십시오.

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
        public interface ICalculator
        {
            [OperationContract]
            double Add(double n1, double n2);
            [OperationContract]
            double Subtract(double n1, double n2);
            [OperationContract]
            double Multiply(double n1, double n2);
            [OperationContract]
            double Divide(double n1, double n2);
        }
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> 이러한 서비스에는 수신 대기를 위해 시스템에 HTTP 주소를 등록할 권한이 있어야 합니다. 관리자 계정에는 이 권한이 있지만, 관리자 이외의 계정에는 HTTP 네임스페이스에 대한 권한을 부여해야 합니다. 네임스페이스 예약을 구성하는 방법에 대한 자세한 내용은 [HTTP 및 HTTPS 구성](feature-details/configuring-http-and-https.md)을 참조하세요. Visual Studio에서 실행하는 경우 service.exe는 관리자 권한으로 실행해야 합니다.

## <a name="next-steps"></a>다음 단계

서비스가 실행되고 있습니다. 다음 태스크에서는 WCF 클라이언트를 만듭니다.

> [!div class="nextstepaction"]
> [방법: WCF 클라이언트 만들기](how-to-create-a-wcf-client.md)

문제 해결 정보는 [초보자를 위한 자습서 문제 해결](troubleshooting-the-getting-started-tutorial.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [시작](samples/getting-started-sample.md)
- [자체 호스팅](samples/self-host.md)
- [서비스 호스팅](hosting-services.md)
