---
title: CA1306：設定資料類型的地區設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539018"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306:必須設定資料類型的地區設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|類別|Microsoft。全球化|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法或函式建立了一或多個 <xref:System.Data.DataTable?displayProperty=fullName> 或 <xref:System.Data.DataSet?displayProperty=fullName> 實例，但未明確設定 (或) 的地區設定屬性 <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 地區設定會決定資料的文化特性特定呈現元素，例如用於數值、貨幣符號和排序次序的格式。 當您建立 <xref:System.Data.DataTable> 或時 <xref:System.Data.DataSet> ，您應該明確地設定地區設定。 根據預設，這些類型的地區設定為目前的文化特性。 針對儲存在資料庫或檔案中且全域共用的資料，地區設定通常應該設定為不因文化特性而異 (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>) 。 當資料在文化特性之間共用時，使用預設地區設定可能會導致 <xref:System.Data.DataTable> 或轉譯或轉譯的內容 <xref:System.Data.DataSet> 不正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請明確設定或的地區設定 <xref:System.Data.DataTable> <xref:System.Data.DataSet> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當程式庫或應用程式適用于有限的本機物件、未共用資料，或預設設定會在所有支援的案例中產生所需的行為時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會建立兩個 <xref:System.Data.DataTable> 實例。

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
