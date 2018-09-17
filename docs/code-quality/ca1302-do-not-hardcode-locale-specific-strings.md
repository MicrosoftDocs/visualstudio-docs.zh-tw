---
title: CA1302：請勿於程式中定義地區設定專屬的字串
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e56c57343ae61709b6d5875c865857a7475363fd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550488"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302：請勿於程式中定義地區設定專屬的字串

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|類別|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法會使用字串常值，表示組件的特定系統資料夾的路徑。

## <a name="rule-description"></a>規則描述
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列舉型別包含參考特殊系統資料夾的成員。 這些資料夾的位置可以有不同的值在不同的作業系統上，使用者可以變更某些位置，和位置會當地語系化。 特殊資料夾的範例位於 [System] 資料夾，也就是"C:\WINDOWS\system32"[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]但"C:\WINNT\system32 」 上的[!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>方法會傳回相關聯的位置<xref:System.Environment.SpecialFolder>列舉型別。 所傳回的位置<xref:System.Environment.GetFolderPath%2A>會當地語系化，並且適用於目前正在執行的電腦。

 此規則會 token 化藉由使用擷取的資料夾路徑<xref:System.Environment.GetFolderPath%2A>成個別的目錄層級的方法。 每個字串常值進行比較的權杖。 如果找到相符項目，則會假設方法建置參考與權杖相關聯的系統位置的字串。 可攜性和可當地語系化，請使用<xref:System.Environment.GetFolderPath%2A>方法來擷取而不是使用字串常值的特殊系統資料夾的位置。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用，位置擷取<xref:System.Environment.GetFolderPath%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果字串常值不用來參考其中一個相關聯的系統位置<xref:System.Environment.SpecialFolder>列舉型別。

## <a name="example"></a>範例
 下列範例會建置通用的應用程式資料資料夾，會產生三個警告，這項規則的路徑。 接下來，此範例會擷取的路徑使用<xref:System.Environment.GetFolderPath%2A>方法。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1303：不要將常值當做已當地語系化的參數傳遞](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)