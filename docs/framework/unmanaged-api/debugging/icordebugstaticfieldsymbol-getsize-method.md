---
title: ICorDebugStaticFieldSymbol::GetSize 메서드
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee8c8a2f88dced7b26d91c17102c42b4338d66ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679307"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a>ICorDebugStaticFieldSymbol::GetSize 메서드
정적 필드의 크기(바이트)를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcbSize`  
 [out] 필드 길이에 대한 포인터입니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
>  이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고자료
- [ICorDebugStaticFieldSymbol 인터페이스](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [디버깅 인터페이스](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
