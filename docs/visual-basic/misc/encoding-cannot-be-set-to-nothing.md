---
title: 인코딩은 Nothing으로 설정할 수 없음
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691331"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>인코딩은 Nothing으로 설정할 수 없음
`encoding` 매개 변수가 `Nothing` 으로 설정되었지만 유효한 값이 필요하기 때문에 파일에서 읽거나 쓰려는 시도가 실패했습니다.  
  
 <xref:System.Text.Encoding> 은 파일에 쓸 때 사용할 인코딩을 결정하기 위해 사용됩니다. 기본값은 UTF-8입니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
-   `encoding` 매개 변수에 대한 유효한 값을 제공합니다.  
  
## <a name="see-also"></a>참고자료
- [파일 인코딩](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [파일 읽기](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [파일에 쓰기](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
