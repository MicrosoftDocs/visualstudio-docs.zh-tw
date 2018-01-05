---
title: "CA1306： 設定地區設定的資料型別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc39ece5eaecfdb36576501caa432abeb365b9cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306：設定資料類型的地區設定
|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法或建構函式建立一個或多個<xref:System.Data.DataTable?displayProperty=fullName>或<xref:System.Data.DataSet?displayProperty=fullName>執行個體，並沒有明確設定地區設定屬性 (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName>或<xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>)。  
  
## <a name="rule-description"></a>規則描述  
 地區設定會決定資料，例如用於數值、 貨幣符號和排序次序的格式設定文化特性特定展示項的目。 當您建立<xref:System.Data.DataTable>或<xref:System.Data.DataSet>，您應該明確設定地區設定。 根據預設，這些類型的地區設定為目前的文化特性。 資料會儲存在資料庫或檔案全域共用，地區設定應該通常設定為文化特性而異 (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>)。 當資料共用跨文化特性時，使用預設的地區設定可能會導致的內容<xref:System.Data.DataTable>或<xref:System.Data.DataSet>呈現或不正確地解譯。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請明確設定的地區設定<xref:System.Data.DataTable>或<xref:System.Data.DataSet>。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它是安全的程式庫或應用程式適用於限制的本機使用者、 不共用的資料，或預設設定會產生所要的行為在所有支援的案例時隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.Data.DataTable>執行個體。  
  
 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>