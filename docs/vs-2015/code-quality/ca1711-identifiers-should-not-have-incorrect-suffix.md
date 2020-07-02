---
title: CA1711：識別碼不應有不正確的尾碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1e753083e9b4bda1e33553021ccb0027a2af2533
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544010"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711:識別項名稱不應該使用不正確的後置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼的尾碼不正確。

## <a name="rule-description"></a>規則描述
 依照慣例，只有擴充特定基底類型或會執行特定介面的類型名稱，或是從這些類型衍生的類型，才應該以特定的保留尾碼做為結尾。 其他類型名稱不得使用這些保留的後置字元。

 下表列出保留尾碼，以及與它們相關聯的基底類型和介面。

|後置詞|基底類型/介面|
|------------|--------------------------|
|屬性|<xref:System.Attribute?displayProperty=fullName>|
|集合|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|字典|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|事件處理常式委派|
|例外狀況|<xref:System.Exception?displayProperty=fullName>|
|權限|<xref:System.Security.IPermission?displayProperty=fullName>|
|佇列|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|
|STREAM|<xref:System.IO.Stream?displayProperty=fullName>|

 此外，**不**應使用下列尾碼：

- 代理人

- 列舉

- Impl-請改用 ' Core '

- Ex 或類似的尾碼，以與相同類型的舊版進行區別

  命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 請從類型名稱中移除尾碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非後置字元在應用程式定義域中具有明確的意義，否則請不要隱藏這項規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1710:識別項應該使用正確的後置字元](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)[筆尖：事件和委派](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
