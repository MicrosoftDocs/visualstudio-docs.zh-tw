---
title: "CA1305： 指定 IFormatProvider |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bb3d993cc79ebf683f0a2622628bfc87d7c065a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305：指定 IFormatProvider
|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法或建構函式呼叫一或多個成員具有多載，可接受<xref:System.IFormatProvider?displayProperty=fullName>參數和方法或建構函式不會呼叫的多載，<xref:System.IFormatProvider>參數。 此規則會忽略呼叫[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]記載成略過的方法<xref:System.IFormatProvider>參數與此外下列方法：  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>規則描述  
 當<xref:System.Globalization.CultureInfo?displayProperty=fullName>或<xref:System.IFormatProvider>未提供物件，多載成員所提供的預設值可能沒有您想要在所有地區設定的效果。 此外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]成員選擇預設文化特性及格式設定為基礎的假設，可能不正確的程式碼。 若要確定程式碼的運作不如預期您的案例，您應該提供根據下列指導方針的特定文化特性資訊：  
  
-   如果此值將會顯示給使用者，使用目前文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。  
  
-   如果將儲存的值，且 （保存至檔案或資料庫） 的軟體存取，使用文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  
  
-   如果您不知道值的目的，有資料取用者，或提供者指定的文化特性。  
  
 請注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>只能用於擷取當地語系化的資源所使用的執行個體<xref:System.Resources.ResourceManager?displayProperty=fullName>類別。  
  
 即使多載成員的預設行為是適用於您的需求，最好明確呼叫的特定文化特性的多載，讓您的程式碼是自我記錄並更容易維護。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，使用的多載，<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider>和指定的引數，根據先前列出的指導方針。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，當您確定預設文化特性/格式提供者是正確的選擇，而且程式碼維護性不重要的開發優先順序。  
  
## <a name="example"></a>範例  
 在下列範例中，`BadMethod`會導致兩個違反此規則。 `GoodMethod`藉由傳遞而異的文化特性，若要更正第一個違規<xref:System.String.Compare%2A>，並藉由傳遞至目前的文化特性修正第二個違規<xref:System.String.ToLower%2A>因為`string3`顯示給使用者。  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例會顯示目前的文化特性的效果，使用預設<xref:System.IFormatProvider>，會選取<xref:System.DateTime>型別。  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 此範例會產生下列輸出。  
  
 **1900 年 6 月 4 日 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>相關的規則  
 [CA1304：必須指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## <a name="see-also"></a>請參閱  
[使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#Cultures)  