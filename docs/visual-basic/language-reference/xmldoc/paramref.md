---
title: <paramref>(Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 1ef8d76699534a7408912424bcdea651d8314364
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283987"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
단어를 형식을 매개 변수로 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>매개 변수  
 `name`  
 참조할 매개 변수의 이름입니다. 이름을 큰따옴표(“ ”)로 묶습니다.  
  
## <a name="remarks"></a>설명  
 `<paramref>` 태그 하면 단어는 매개 변수를 지정할 수 있습니다. XML 파일을 다른 방식으로이 매개 변수 형식을 처리할 수 있습니다.  
  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)로 컴파일하여 문서 주석을 파일로 처리합니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 합니다 `<paramref>` 참조 하는 태그를 `id` 매개 변수입니다.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>참고자료
- [XML 주석 태그](../../../visual-basic/language-reference/xmldoc/index.md)
