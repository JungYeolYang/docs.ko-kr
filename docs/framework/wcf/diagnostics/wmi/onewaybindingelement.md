---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: d84184febd6db3f233aae6fe558b8e0f50a9cb82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608838"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>구문  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>메서드  
 OneWayBindingElement 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  
 OneWayBindingElement 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 데이터 형식: ChannelPoolSettings  
  
 액세스 형식: 읽기 전용  
  
 채널 풀 설정입니다.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 허용되는 최대 채널 수입니다.  
  
### <a name="packetroutable"></a>PacketRoutable  
 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 패킷을 라우팅할 수 있는지 여부를 나타내는 값입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고자료
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
