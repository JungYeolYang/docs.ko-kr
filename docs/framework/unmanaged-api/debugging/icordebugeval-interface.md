---
title: ICorDebugEval Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da68bc4218d59320997a341f8c4a860201ba643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620333"
---
# <a name="icordebugeval-interface1"></a>ICorDebugEval Interface1
디버깅 중인 코드의 컨텍스트 내에서 디버거가 코드를 실행할 수 있도록 하는 메서드를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Abort 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|이 계산이 중단 `ICorDebugEval` 개체가 현재 수행 합니다.|  
|[CallFunction 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|지정된 된 함수에 대 한 호출을 설정합니다. (.NET Framework 버전 2.0에서에서 사용 되지 않음; 사용 [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) 대신 합니다.)|  
|[CreateValue 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|초기 값이 0 또는 null을 사용 하 여 지정 된 형식의 "ICorDebugValue" 개체에는 인터페이스 포인터를 가져옵니다. (.NET Framework 2.0에서 사용 되지 않음; 사용 [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) 대신 합니다.)|  
|[GetResult 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|한 인터페이스 포인터를 가져옵니다는 `ICorDebugValue` 평가의 결과 포함 하는 합니다.|  
|[GetThread 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|이 평가 실행 하거나 실행 위치는 "ICorDebugThread"에 대 한 인터페이스 포인터를 가져옵니다.|  
|[IsActive 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|나타내는 값을 가져옵니다 여부를이 `ICorDebugEval` 개체는 현재 실행 합니다.|  
|[NewArray 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|지정 된 요소 형식 및 차원에는 새 배열을 할당합니다. (.NET Framework 2.0에서 사용 되지 않음; 사용 [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) 대신 합니다.)|  
|[NewObject 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|새 개체 인스턴스를 할당 하 고 지정된 된 생성자 메서드를 호출 합니다. (.NET Framework 2.0에서 사용 되지 않음; 사용 [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) 대신 합니다.)|  
|[NewObjectNoConstructor 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|생성자 메서드를 호출 하지 않고 지정 된 형식의 새 개체 인스턴스를 할당 합니다. (.NET Framework 2.0에서 사용 되지 않음; 사용 [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) 대신 합니다.)|  
|[NewString 메서드](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|지정된 된 콘텐츠를 사용 하 여 새 문자열 개체를 할당 합니다.|  
  
## <a name="remarks"></a>설명  
 `ICorDebugEval` 평가 수행 하는 데 사용 되는 특정 스레드 컨텍스트에서 개체가 만들어집니다. 모든 개체 및 형식 지정된 평가에 사용 된 동일한 응용 프로그램 도메인 내에 있어야 합니다. 해당 응용 프로그램 도메인 스레드의 현재 응용 프로그램 도메인과 같은 있어야 합니다. 평가 중첩할 수 있습니다.  
  
 디버거 호출 될 때까지 계산의 작업을 완료 하지 마세요 [icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md), 다음 수신는 [icordebugmanagedcallback:: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) 콜백 합니다. 다른 스레드가 실행을 허용 하지 않고 평가 기능을 사용 하는 경우 스레드 중 하나를 사용 하 여 일시 중단 [icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) 또는 [icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)호출 하기 전에 [icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)합니다.  
  
 평가 진행에서 중일 때 사용자 코드가 실행 되 고, 때문에 디버그 이벤트 클래스 로드 및 중단점을 포함 하 여 발생할 수 있습니다. 디버거 콜백의 경우, 이러한 이벤트에 대 한 일반적인 방법으로 받습니다. 평가의 상태는 정상적인 프로그램 상태 검사의 일부로 나타납니다. 스택 체인 됩니다는 `CHAIN_FUNC_EVAL` 체인 ("CorDebugStepReason" 열거형을 참조 하며 [icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) 메서드). 전체 디버거 API는 계속 정상적으로 작동 합니다.  
  
 교착 상태 또는 무한 루프 상황이 발생 하는 경우에 사용자 코드가 완료 되지 않습니다. 이러한 경우에 호출 해야 합니다 [icordebugeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) 프로그램을 다시 시작 하기 전에 합니다.  
  
> [!NOTE]
>  이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)을 참조하십시오.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고자료



- [디버깅 인터페이스](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
