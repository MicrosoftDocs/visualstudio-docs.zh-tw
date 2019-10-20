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
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661480"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302：請勿於程式中定義地區設定專屬的字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft。全球化|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法會使用字串常值，表示特定系統資料夾的部分路徑。

## <a name="rule-description"></a>規則描述
 @No__t_0 列舉包含參考特殊系統資料夾的成員。 這些資料夾的位置在不同的作業系統上可能會有不同的值，使用者可以變更部分位置，並將位置當地語系化。 特殊資料夾的範例是 System 資料夾，這是 [!INCLUDE[winxp](../includes/winxp-md.md)] 上的 "C:\WINDOWS\system32"，但 [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] 上的 "C:\WINNT\system32"。 @No__t_0 方法會傳回與 <xref:System.Environment.SpecialFolder> 列舉相關聯的位置。 @No__t_0 所傳回的位置會當地語系化，並適用于目前執行中的電腦。

 此規則會 token 化使用 <xref:System.Environment.GetFolderPath%2A> 方法抓取到不同目錄層級的資料夾路徑。 每個字串常值都會與標記進行比較。 如果找到相符的結果，則會假設方法正在建立一個字串，而該字串會參考與該 token 相關聯的系統位置。 針對可攜性和當地語系化能力，請使用 <xref:System.Environment.GetFolderPath%2A> 方法來取出特殊系統資料夾的位置，而不是使用字串常值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請使用 <xref:System.Environment.GetFolderPath%2A> 方法來取出位置。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果未使用字串常值來參考與 <xref:System.Environment.SpecialFolder> 列舉相關聯的其中一個系統位置，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會建立通用應用程式資料檔案夾的路徑，這會產生來自此規則的三個警告。 接下來，此範例會使用 <xref:System.Environment.GetFolderPath%2A> 方法來抓取路徑。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1303：不要將常值當做已當地語系化的參數傳遞](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
