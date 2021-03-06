---
title: CoreResponseData.m_StatusCode 필드
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 53338c75d31cef3ab89879632710dba3e52091ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751911"
---
# <a name="coreresponsedatamstatuscode-field"></a>CoreResponseData.m\_StatusCode 필드

`CoreResponseData.m_StatusCode` 이 <xref:System.Net.HttpStatusCode> 응답의 상태를 포함 합니다.

## <a name="syntax"></a>구문
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> 이 API는 사용자 코드에서 직접 사용할 수는 적용 되지 않습니다. 를 대신 사용 해야는 <xref:System.Diagnostics.DiagnosticSource> 네트워킹 코드를 연결 합니다. 참조 [DiagnosticSource 사용자 가이드](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)합니다.
> 
> Microsoft은 프로덕션 응용 프로그램의 어떤 상황에서이 클래스의 사용을 지원 하지 않습니다.

## <a name="requirements"></a>요구 사항

**Namespace:** <xref:System.Net>

**어셈블리:** 시스템 (System.dll)

**.NET framework 버전:** 2.0부터 사용 가능 합니다.
