---
title: '방법: 3차원 변환에 애니메이션 효과 주기'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: e73035a48e32e3eec20b44c82b5b9ec6763c1e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653036"
---
# <a name="how-to-animate-3-d-translations"></a>방법: 3차원 변환에 애니메이션 효과 주기
이 항목에 설정 된 번역 변형 애니메이션 효과를 주는 방법을 보여 줍니다는 [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 모델입니다.  
  
 아래 코드의 응용 프로그램을 보여 줍니다를 <xref:System.Windows.Media.Media3D.TranslateTransform3D> 개체를 <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> 의 속성을 <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 합니다 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> 이 <xref:System.Windows.Media.Media3D.TranslateTransform3D> 개체 아래 코드를 사용 하 여 애니메이션 효과가 적용 됩니다.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>예제  
 다음 코드에는 전체 샘플을 보여 줍니다.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>참고자료
- [애니메이션 개요](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [3차원 장면 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [3차원 그래픽 개요](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Transform 개요](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
