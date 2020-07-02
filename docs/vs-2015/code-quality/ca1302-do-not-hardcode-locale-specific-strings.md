---
title: CA1302：不要將地區設定特定字串硬式編碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539005"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302:不要以硬式編碼的方式加入適用於特定地區設定的字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|類別|Microsoft。全球化|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法會使用字串常值，表示特定系統資料夾的部分路徑。

## <a name="rule-description"></a>規則描述
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列舉包含參考特殊系統資料夾的成員。 這些資料夾的位置在不同的作業系統上可能會有不同的值，使用者可以變更部分位置，並將位置當地語系化。 特殊資料夾的範例是 System 資料夾，其為 "C:\WINDOWS\system32"， [!INCLUDE[winxp](../includes/winxp-md.md)] 但 "C:\WINNT\system32" on [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] 。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>方法會傳回與列舉相關聯的位置 <xref:System.Environment.SpecialFolder> 。 所傳回的位置 <xref:System.Environment.GetFolderPath%2A> 已當地語系化，適用于目前執行中的電腦。

 此規則會 token 化使用 <xref:System.Environment.GetFolderPath%2A> 方法抓取到不同目錄層級的資料夾路徑。 每個字串常值都會與標記進行比較。 如果找到相符的結果，則會假設方法正在建立一個字串，而該字串會參考與該 token 相關聯的系統位置。 如需可攜性和當地語系化能力，請使用 <xref:System.Environment.GetFolderPath%2A> 方法來抓取特殊系統資料夾的位置，而不是使用字串常值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用方法來取出位置 <xref:System.Environment.GetFolderPath%2A> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果未使用字串常值來參考與列舉相關聯的其中一個系統位置，則可以放心地隱藏此規則的警告 <xref:System.Environment.SpecialFolder> 。

## <a name="example"></a>範例
 下列範例會建立通用應用程式資料檔案夾的路徑，這會產生來自此規則的三個警告。 接下來，此範例會使用方法來抓取路徑 <xref:System.Environment.GetFolderPath%2A> 。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1303:不要將常值當作已當地語系化的參數傳遞](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
