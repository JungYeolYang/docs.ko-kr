---
title: "'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다."
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282592"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다.
에 대 한 초기 호출을 `Dir` 함수는 포함 되지 않습니다는 `PathName` 인수입니다. 첫 번째 호출은 `Dir` 포함 해야 합니다는 `PathName`, 하지만 후속 호출 `Dir` 다음 항목을 검색 하는 매개 변수를 포함할 필요가 없습니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1.  제공 된 `PathName` 함수 호출의 인수입니다.  
  
## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
