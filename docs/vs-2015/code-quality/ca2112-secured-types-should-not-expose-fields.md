---
title: CA2112：受保護類型不應該公開欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546532"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112:受保護類型不應該公開欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用欄位，並受到 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)保護。

## <a name="rule-description"></a>規則描述
 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將這些欄位設為非公用，並新增可傳回欄位資料的公用屬性或方法。 類型的 LinkDemand 安全性檢查可保護對類型屬性和方法的存取。 但是，代碼啟用安全性並不適用于欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對安全性問題和良好的設計，您應該將公用欄位設為非公用，以修正違規。 如果欄位不包含應該保持安全的資訊，而且您不依賴欄位的內容，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例是由程式庫型別 (`SecuredTypeWithFields`) 包含不安全的欄位、 `Distributor` 可建立程式庫類型之實例的型別 () ，以及將實例的傳遞給型別不具有建立它們的許可權，以及可讀取實例欄位的應用程式程式碼，即使它沒有保護型別的許可權也一樣。

 下列程式庫程式碼違反規則。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>範例
 由於保護受保護類型的連結要求，應用程式無法建立實例。 下列類別可讓應用程式取得安全類型的實例。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>範例
 下列應用程式會說明如何（沒有存取安全類型方法的許可權），程式碼可以存取其欄位。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 此範例會產生下列輸出。

 **建立 SecuredTypeWithFields 的實例。** 
**安全類型欄位：22、33** 
正在**變更安全類型的欄位** 
 .。。快取**的物件欄位：99、33**
## <a name="related-rules"></a>相關規則
 [CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱
 [連結需求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
