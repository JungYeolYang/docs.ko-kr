---
title: '방법: (LINQ) (Visual Basic)의 두 목록 간의 차집합 구하기'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: e1c012dbe252c494c5f77e61b56deccbb07490fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579721"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>방법: (LINQ) (Visual Basic)의 두 목록 간의 차집합 구하기
이 예제에서는 LINQ를 사용하여 두 개의 문자열 목록을 비교하고 names1.txt에 있지만 names2.txt에는 없는 줄만 출력하는 방법을 보여 줍니다.  
  
### <a name="to-create-the-data-files"></a>데이터 파일을 만들려면  
  
1.  에 표시 된 대로 names1.txt 및 names2.txt를 솔루션 폴더로 복사 [방법: (LINQ) (Visual Basic) 문자열 컬렉션 결합 및 비교](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)합니다.  
  
## <a name="example"></a>예제  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 일부 유형의 쿼리 작업 Visual basic의 경우와 같은 <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>를 <xref:System.Linq.Enumerable.Union%2A>, 및 <xref:System.Linq.Enumerable.Concat%2A>, 메서드 기반 구문 으로만 표현할 수 있습니다.  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 System.Core.dll에 대한 참조와 System.Linq 네임스페이스에 대한 `Imports` 문을 사용하여 .NET Framework 버전 3.5 이상을 대상으로 하는 프로젝트를 만듭니다.  
  
## <a name="see-also"></a>참고자료
- [LINQ 및 문자열 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
