---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 0dc74b784d8a9ed3ab27bb4b8d3de34143f6ce07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639486"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a>CoordinatorRecoveryLogEntryCorrupt
ID: 139  
  
 심각도: Error  
  
 범주: TransactionBridge  
  
## <a name="description"></a>설명  
 이 이벤트는 코디네이터 복구 로그 항목이 손상되어 deserialize할 수 없음을 나타냅니다. 이 오류로 인해 데이터가 손실될 수 있습니다. 이벤트에는 트랜잭션 ID, 복구 데이터(Base64 인코딩), 예외, 프로세스 이름 및 프로세스 ID가 표시됩니다.  
  
## <a name="see-also"></a>참고자료
- [이벤트 로깅](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [이벤트 일반 참조](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
