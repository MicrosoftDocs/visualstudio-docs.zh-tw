---
title: CA1306： 設定資料類型的地區設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8384f20868a731cb7a37ca547fef40b5c3b16da6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244214"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306：設定資料類型的地區設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法或建構函式會建立一或多個<xref:System.Data.DataTable?displayProperty=fullName>或是<xref:System.Data.DataSet?displayProperty=fullName>執行個體，並在未明確設定地區設定屬性 (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName>或<xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>)。

## <a name="rule-description"></a>規則描述
 地區設定會決定資料，例如用於數值、 貨幣符號和排序順序設定格式化的文化特性特定展示項目。 當您建立<xref:System.Data.DataTable>或<xref:System.Data.DataSet>，您應該明確設定的地區設定。 根據預設，這些類型的地區設定會是目前的文化特性。 資料會儲存在資料庫或檔案，都共用這個全域地區設定應該通常設定為文化特性而異 (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>)。 當資料共用跨文化特性時，使用預設的地區設定可能會導致的內容<xref:System.Data.DataTable>或<xref:System.Data.DataSet>呈現或不正確地解譯。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，明確設定的地區設定<xref:System.Data.DataTable>或<xref:System.Data.DataSet>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全的程式庫或應用程式適用於限制的本機使用者、 不共用資料，或預設設定會產生所要的行為，在所有支援的案例時隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會建立兩個<xref:System.Data.DataTable>執行個體。

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>



