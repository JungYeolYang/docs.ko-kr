---
title: '상호 운용성 - C# 프로그래밍 가이드'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - COM interop
  - interoperability
  - 'platform invoke, accessing APIs with C#'
  - 'C# language, interoperability'
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
---
# <a name="interoperability-c-programming-guide"></a>상호 운용성(C# 프로그래밍 가이드)
상호 운용성은 비관리 코드에 대한 기존 투자를 보존하고 활용할 수 있도록 합니다. CLR(공용 언어 런타임)의 제어 하에서 실행되는 코드를 *관리 코드*라고 하고, CLR 외부에서 실행되는 코드를 *비관리 코드*라고 합니다. COM, COM+, C++ 구성 요소, ActiveX 구성 요소 및 Microsoft Win32 API는 비관리 코드의 예입니다.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]에서는 플랫폼 호출 서비스, <xref:System.Runtime.InteropServices> 네임스페이스, C++ 상호 운용성 및 COM 상호 운용성(COM interop)을 통해 비관리 코드와의 상호 운용이 가능합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [상호 운용성 개요](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 C# 관리 코드와 비관리 코드 간에 상호 운용되도록 하는 방법을 설명합니다.  
  
 [방법: Visual C# 기능을 사용하여 Office Interop 개체에 액세스](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Office 프로그래밍을 용이하게 하도록 Visual C#에 도입된 기능에 대해 설명합니다.  
  
 [방법: COM Interop 프로그래밍에서 인덱싱된 속성 사용](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 인덱싱된 속성을 사용하여 매개 변수가 있는 COM 속성에 액세스하는 방법을 설명합니다.  
  
 [방법: 플랫폼 호출을 사용하여 웨이브 파일 재생](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 플랫폼 호출 서비스를 사용하여 Windows 운영 체제에서 .wav 사운드 파일을 재생하는 방법을 설명합니다.  
  
 [연습: Office 프로그래밍](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Excel 통합 문서와 통합 문서에 대한 링크를 포함하는 Word 문서를 만드는 방법을 보여 줍니다.  
  
 [COM 클래스 예제](../../../csharp/programming-guide/interop/example-com-class.md)  
 C# 클래스를 COM 개체로 노출하는 방법을 보여 줍니다.  
  
## <a name="c-language-specification"></a>C# 언어 사양  

자세한 내용은 [C# 언어 사양](../../language-reference/language-specification/index.md)의 [기본 개념](~/_csharplang/spec/unsafe-code.md)을 참조하세요. C# 언어 사양은 C# 구문 및 사용법에 대한 신뢰할 수 있는 소스입니다.
  
## <a name="see-also"></a>참고 항목

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md)
- [비관리 코드와의 상호 운용](../../../../docs/framework/interop/index.md)
- [연습: Office 프로그래밍](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
