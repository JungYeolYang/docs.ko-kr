---
title: '방법: 숫자 (Visual Basic)를 16 진수 문자열 변환'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: 76acee8913df35d4d071017078b38a3c474c3357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633819"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>방법: 숫자 (Visual Basic)를 16 진수 문자열 변환
사용 하는 정수를 16 진수 문자열로 변환 하는이 예제는 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 메서드.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>16 진수 문자열을 숫자로 변환 하려면  
  
-   사용 된 <xref:System.Convert.ToInt32(System.String,System.Int32)> 정수를 16 진수로 표시 된 숫자를 변환 하는 방법입니다.  
  
     첫 번째 인수는 <xref:System.Convert.ToInt32(System.String,System.Int32)> 메서드는 변환할 문자열입니다. 두 번째 인수는 숫자에서 기 수를 나타냅니다. 16 진수는 16입니다.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- 16 진수 문자열 제한이 다음 note:

   - 포함할 수 없습니다는 `&h` 접두사입니다.
   - 포함할 수 없습니다는 `_` 숫자 구분 기호입니다.

   접두사 또는 숫자 구분 기호 있는 경우에 대 한 호출을 <xref:System.Convert.ToInt32(System.String,System.Int32)> 메서드가 throw를 <xref:System.FormatException>입니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
