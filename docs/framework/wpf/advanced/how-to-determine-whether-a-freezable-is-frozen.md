---
title: '방법: Freezable의 고정 여부 확인'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: dee5edc3d8845b00fa6c9aa05c414fd4f912aeb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592275"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>방법: Freezable의 고정 여부 확인
확인 하는 방법을 보여 주는이 예제 여부는 <xref:System.Windows.Freezable> 개체의 고정 합니다. 고정 된 수정 하려고 하면 <xref:System.Windows.Freezable> 개체를 throw 한 <xref:System.InvalidOperationException>합니다. 이 예외를 방지 하려면 사용 합니다 <xref:System.Windows.Freezable.IsFrozen%2A> 의 속성을 <xref:System.Windows.Freezable> 고정 되었는지 여부를 결정 하는 개체.  
  
## <a name="example"></a>예제  
 다음 예에서는 중지를 <xref:System.Windows.Media.SolidColorBrush> 다음 사용 하 여 테스트를 <xref:System.Windows.Freezable.IsFrozen%2A> 속성의 고정 여부 확인을 합니다.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 에 대 한 자세한 내용은 <xref:System.Windows.Freezable> 개체를 참조 합니다 [Freezable 개체 개요](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)합니다.  
  
## <a name="see-also"></a>참고자료
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Freezable 개체 개요](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [방법 항목](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
