---
title: '방법: GridView를 사용하여 ListView 콘텐츠 표시'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 0e2b37cb061cc92b34c3a4f94bcd42e8ffc69ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606009"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>방법: GridView를 사용하여 ListView 콘텐츠 표시
정의 하는 방법을 보여 주는이 예제는 <xref:System.Windows.Controls.GridView> 에 대 한 보기 모드를 <xref:System.Windows.Controls.ListView> 제어 합니다.  
  
## <a name="example"></a>예제  
 보기 모드를 정의할 수 있습니다는 <xref:System.Windows.Controls.GridView> 를 지정 하 여 <xref:System.Windows.Controls.GridViewColumn> 개체입니다. 다음 예제에서는 정의 하는 방법을 보여 줍니다 <xref:System.Windows.Controls.GridViewColumn> 에 지정 된 데이터 콘텐츠를 바인딩하는 개체는 <xref:System.Windows.Controls.ListView> 제어 합니다. 이 <xref:System.Windows.Controls.GridView> 3을 지정 하는 예제 <xref:System.Windows.Controls.GridViewColumn> 에 매핑되는 개체를 `FirstName`, `LastName`, 및 `EmployeeNumber` 필드를 `EmployeeInfoDataSource` 로 설정 되어 있는 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 의 <xref:System.Windows.Controls.ListView> 컨트롤입니다.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 다음 그림에서는이 예제에서는 표시 되는 방식을 보여 줍니다.  
  
 ![GridView 출력이 있는 ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>참고자료
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView 개요](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView 개요](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [방법 항목](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
