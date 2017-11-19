---
title: "CA2225： 運算子多載有具名的替代方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07d15e5ec123e645a7607f16b6020487d4c0fc2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225：運算子多載必須有具名的替代方法
|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 偵測到運算子多載，且找不到預期的具名替代方法。  
  
## <a name="rule-description"></a>規則描述  
 運算子多載可讓您使用符號來表示類型的計算。 例如，新增多載加號 （+） 的型別通常必須命名為 'Add' 的替代成員。 具名的替代成員存取運算子，與相同的功能，並提供的開發人員程式在語言不支援多載的運算子。  
  
 此規則會檢查下表中列出的運算子。  
  
|C#|Visual Basic|C++|替代名稱|  
|---------|------------------|-----------|--------------------|  
|+ （二進位）|+|+ （二進位）|新增|  
|+=|+=|+=|新增|  
|&|及|&|BitwiseAnd|  
|&=|和 =|&=|BitwiseAnd|  
|&#124;|或|&#124;|BitwiseOr|  
|&#124;=|或 =|&#124;=|BitwiseOr|  
|--|N/A|--|遞減|  
|/|/|/|分割|  
|/=|/=|/=|分割|  
|==|=|==|等於|  
|^|Xor|^|Xor|  
|^=|Xor =|^=|Xor|  
|>|>|>|比較|  
|>=|>=|>=|比較|  
|++|N/A|++|遞增|  
|<>|!=|等於|  
|<<|<<|<<|LeftShift|  
|<<=|<<=|<<=|LeftShift|  
|<|<|<|比較|  
|<=|<=|\<=|比較|  
|&&|N/A|&&|LogicalAnd|  
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|  
|!|N/A|!|LogicalNot|  
|%|Mod|%|Mod 或餘數|  
|%=|N/A|%=|Mod|  
|* （二進位）|*|*|乘法|  
|*=|N/A|*=|乘法|  
|~|not|~|OnesComplement|  
|>>|>>|>>|RightShift|  
=|N/A|>>=|RightShift|  
|-（二進位）|-（二進位）|-（二進位）|差集|  
|-=|N/A|-=|差集|  
|true|IsTrue|N/A|IsTrue （屬性）|  
|-（一元）|N/A|-|變換正負號|  
|+ （一元）|N/A|+|加號|  
|false|IsFalse|False|IsTrue （屬性）|  
  
 N/A = = 無法多載，以選取的語言。  
  
 此規則也會檢查型別中隱含和明確的轉型運算子 (`SomeType`) 藉由檢查方法，名為`ToSomeType`和`FromSomeType`。  
  
 在 C# 中，多載二元運算子，對應的指派運算子，如果有的話，時，也隱含多載。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，運算子; 實作替代方法它使用建議的替代名稱命名。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告，如果您要實作共用程式庫。 應用程式可以忽略這個規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會定義違反此規則的結構。 若要更正此範例中，新增公用`Add(int x, int y)`結構的方法。  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)