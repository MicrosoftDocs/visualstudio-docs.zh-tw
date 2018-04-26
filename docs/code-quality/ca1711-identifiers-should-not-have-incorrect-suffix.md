---
title: CA1711：識別項名稱不應該使用不正確的後置字元
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4faed3f5d49c6c08ca0a9bc90465f4e21ef3fec8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711：識別項名稱不應該使用不正確的後置字元
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別項具有不正確的後置詞。

## <a name="rule-description"></a>規則描述
 依照慣例，只有擴充特定基底類型或實作特定介面或衍生自這些類型，類型的名稱應以特定保留的後置字元結尾。 其他類型名稱不得使用這些保留的後置字元。

 下表列出保留的後置字元的基底類型和其相關聯的介面。

|尾碼|基底型別/介面|
|------------|--------------------------|
|屬性|<xref:System.Attribute?displayProperty=fullName>|
|集合|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|字典|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|事件處理常式|事件處理常式委派|
|例外|<xref:System.Exception?displayProperty=fullName>|
|權限|<xref:System.Security.IPermission?displayProperty=fullName>|
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|
|堆疊|<xref:System.Collections.Stack?displayProperty=fullName>|
|資料流|<xref:System.IO.Stream?displayProperty=fullName>|

 此外，下列尾碼應該**不**使用：

-   Delegate - 委派

-   列舉

-   Impl-使用 'Core' 代替

-   Ex 或類似的後置詞區別較早版本的相同型別

 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除型別名稱後置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非後置字元在應用程式定義域中具有明確的意義，否則請不要隱藏這項規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1710：識別項應該使用正確的後置字元](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>另請參閱
 [屬性](/dotnet/standard/design-guidelines/attributes)[處理和引發事件](/dotnet/standard/events/index)