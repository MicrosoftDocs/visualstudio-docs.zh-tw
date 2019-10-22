---
title: CA2112：受保護的類型不應該公開欄位 |Microsoft Docs
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
ms.openlocfilehash: b9c91a7c9833d3d9d5ae283c28ae4d437bd07734
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658754"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112：受保護類型不應公開欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用欄位，並受到[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)保護。

## <a name="rule-description"></a>規則描述
 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將欄位設為非公用，並加入公開屬性或傳回欄位資料的方法。 類型的 LinkDemand 安全性檢查可保護類型的屬性和方法的存取。 不過，代碼啟用安全性並不適用于欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 基於安全性問題和良好的設計，您應該將公用欄位設為非公用，以修正違規。 如果欄位未保存應保持安全的資訊，而且您不依賴欄位的內容，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例是由程式庫類型（`SecuredTypeWithFields`）所組成，其中包含不安全的欄位、可建立程式庫類型實例的類型（`Distributor`），以及將實例傳遞給類型時沒有建立它們的許可權，以及可讀取的應用程式程式碼實例的欄位，即使它沒有保護該類型的許可權也一樣。

 下列程式庫程式碼違反規則。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>範例
 應用程式由於保護安全類型的連結要求，而無法建立實例。 下列類別可讓應用程式取得安全類型的實例。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>範例
 下列應用程式說明如何在沒有許可權的情況下存取受保護類型的方法，並可存取其欄位。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 此範例會產生下列輸出。

 **建立 SecuredTypeWithFields 的實例。** 
**安全的類型欄位：22、33** 
**變更受保護類型的欄位 ...** 
 快取**的物件欄位：99、33**
## <a name="related-rules"></a>相關規則
 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>請參閱
 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
