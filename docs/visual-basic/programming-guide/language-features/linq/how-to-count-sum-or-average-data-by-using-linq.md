---
title: '방법: 개수, 합 또는 평균 데이터 LINQ (Visual Basic)를 사용 하 여'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: e95f9d75ab9db07b55257bbf6ca951a898b2fb2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735093"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>방법: 개수, 합 또는 평균 데이터 LINQ (Visual Basic)를 사용 하 여
언어 통합 쿼리 (LINQ)를 사용 하면 쉽게 데이터베이스 정보에 액세스 하 고 쿼리를 실행 합니다.  
  
 다음 예제에는 SQL Server 데이터베이스에 대 한 쿼리를 수행 하는 새 응용 프로그램을 만드는 방법을 보여 줍니다. 샘플 개수, 합계, 및를 사용 하 여 결과 평균 합니다 `Aggregate` 고 `Group By` 절. 자세한 내용은 [Aggregate 절](../../../../visual-basic/language-reference/queries/aggregate-clause.md) 하 고 [그룹 By 절](../../../../visual-basic/language-reference/queries/group-by-clause.md)합니다.  
  
 이 항목의 예제는 Northwind 샘플 데이터베이스를 사용합니다. 개발 컴퓨터에이 데이터베이스가 없는 경우에 Microsoft 다운로드 센터에서 다운로드할 수 있습니다. 자세한 내용은 [샘플 데이터베이스 다운로드](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)합니다.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>데이터베이스에 대 한 연결을 만들려면  
  
1.  Visual Studio에서 엽니다 **서버 탐색기**/**데이터베이스 탐색기** 를 클릭 하 여 **서버 탐색기**/**데이터베이스 탐색기** 에 **보기** 메뉴.  
  
2.  마우스 오른쪽 단추로 클릭 **데이터 연결** 에 **서버 탐색기**/**데이터베이스 탐색기** 을 클릭 한 다음 **연결 추가**합니다.  
  
3.  Northwind 샘플 데이터베이스에 올바른 연결을 지정 합니다.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL 파일을 포함 하는 프로젝트를 추가 하려면  
  
1.  Visual Studio의 **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다. Visual basic **Windows Forms 응용 프로그램** 프로젝트 유형으로 합니다.  
  
2.  **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다. 선택 된 **LINQ to SQL 클래스** 항목 템플릿.  
  
3.  파일 이름을 `northwind.dbml`로 지정합니다. **추가**를 클릭합니다. 개체 관계형 디자이너 (O/R 디자이너) northwind.dbml 파일이 열립니다.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R 디자이너를 쿼리 하는 테이블을 추가 하려면  
  
1.  **서버 탐색기**/**데이터베이스 탐색기**, Northwind 데이터베이스에 연결을 확장 합니다. **테이블** 폴더를 확장합니다.  
  
     O/R 디자이너를 닫은 경우 이전에 추가한 northwind.dbml 파일을 두 번 클릭 하 여 다시 열 수 있습니다.  
  
2.  Customers 테이블을 클릭 하 고 디자이너의 왼쪽된 창에 놓습니다. Orders 테이블을 클릭 하 고 디자이너의 왼쪽된 창에 놓습니다.  
  
     디자이너를 새로 만듭니다 `Customer` 고 `Order` 프로젝트에 대 한 개체입니다. 디자이너 자동으로 테이블 간의 관계를 검색 및 확인 자식 관련된 개체에 대 한 속성을 만듭니다. 예를 들어 IntelliSense는 표시 됩니다는 `Customer` 개체에는 `Orders` 해당 고객에 게 관련 된 모든 주문에 대 한 속성입니다.  
  
3.  변경 내용을 저장 하 고 디자이너를 닫습니다.  
  
4.  프로젝트를 저장합니다.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>데이터베이스를 쿼리하고 결과 표시 하는 코드를 추가 하려면  
  
1.  **도구 상자**를 끌어를 <xref:System.Windows.Forms.DataGridView> Form1 프로젝트에 대 한 기본 Windows Form 컨트롤입니다.  
  
2.  코드를 추가 하는 Form1을 두 번 클릭 합니다 `Load` 폼의 이벤트입니다.  
  
3.  O/R 디자이너에 테이블을 추가한 경우 디자이너 추가 <xref:System.Data.Linq.DataContext> 프로젝트에 대 한 개체입니다. 이 개체는 해당 테이블에 액세스 하 고 개별 개체 및 각 테이블에 대 한 컬렉션에 액세스할 수 있어야 하는 코드를 포함 합니다. <xref:System.Data.Linq.DataContext> .dbml 파일의 이름에 따라 프로젝트에 대해 개체입니다. 이 프로젝트에는 <xref:System.Data.Linq.DataContext> 개체의 이름은 `northwindDataContext`합니다.  
  
     인스턴스를 만들 수는 <xref:System.Data.Linq.DataContext> 코드와 쿼리가에서 O/R 디자이너에서 지정 된 테이블입니다.  
  
     다음 코드를 추가 합니다 `Load` 의 속성으로 노출 되는 테이블을 쿼리 하는 이벤트에 <xref:System.Data.Linq.DataContext> 및 개수, 합계, 및 결과 평균 합니다. 샘플을 사용 합니다 `Aggregate` 단일 결과 쿼리 하는 절 및 `Group By` 평균을 표시 하는 절 결과 그룹화 합니다.  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  F5 키를 눌러 프로젝트를 실행 하 고 결과 확인 합니다.  
  
## <a name="see-also"></a>참고자료
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [쿼리](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 메서드(O/R 디자이너)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Aggregate 절](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Group By 절](../../../../visual-basic/language-reference/queries/group-by-clause.md)
