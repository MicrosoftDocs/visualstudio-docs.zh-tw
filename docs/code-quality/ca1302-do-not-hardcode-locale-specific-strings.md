---
title: CA1302：請勿於程式中定義地區設定專屬的字串
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0de562f8f7af4e76b31bc49c33742009db485415
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302：請勿於程式中定義地區設定專屬的字串
|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|分類|Microsoft.Globalization|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會使用字串常值，表示組件的特定系統資料夾的路徑。

## <a name="rule-description"></a>規則描述
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列舉型別包含參考特殊系統資料夾的成員。 這些資料夾的位置可以在不同作業系統上有不同的值、 使用者可以變更某些位置，和位置會當地語系化。 特殊資料夾的範例是在系統資料夾"C:\WINDOWS\system32"[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]但"C:\WINNT\system32 」 上的[!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>方法會傳回相關聯的位置<xref:System.Environment.SpecialFolder>列舉型別。 所傳回的位置<xref:System.Environment.GetFolderPath%2A>會當地語系化，並且適用於目前執行的電腦。

 此規則會 token 化的資料夾路徑，藉由使用擷取<xref:System.Environment.GetFolderPath%2A>成個別的目錄層級的方法。 每個字串常值進行比較之語彙基元。 如果找到相符項目，則會假設方法會建立字串，它是指與權杖相關聯的系統位置。 可攜性和當地語系化能力，請使用<xref:System.Environment.GetFolderPath%2A>方法來擷取特殊系統資料夾，而不要使用字串常值的位置。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，擷取的位置使用<xref:System.Environment.GetFolderPath%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果字串常值不會用來參照其中一個相關聯的系統位置<xref:System.Environment.SpecialFolder>列舉型別。

## <a name="example"></a>範例
 下列範例會建置通用的應用程式資料資料夾，此規則會產生三個警告的路徑。 接下來，此範例會擷取路徑使用<xref:System.Environment.GetFolderPath%2A>方法。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1303：不要將常值當做已當地語系化的參數傳遞](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)