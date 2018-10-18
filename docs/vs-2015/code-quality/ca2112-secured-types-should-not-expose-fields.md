---
title: CA2112： 受保護的類型不應該公開欄位 |Microsoft Docs
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
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3c42de78a75a689b2f248edd66df8109bcd00583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189655"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112：受保護類型不應公開欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用欄位，而且受到[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)。

## <a name="rule-description"></a>規則描述
 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將欄位設為非公用，並將公用屬性或方法傳回的欄位資料。 LinkDemand 的比較型別上的安全性檢查保護的類型屬性和方法的存取。 不過，程式碼存取安全性不會不會套用至欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對安全性問題和良好的設計，您應該修正違規，藉由公用欄位的非公用。 如果欄位不應該保持安全、 的資訊，您可以隱藏此規則的警告，您不會依賴欄位的內容。

## <a name="example"></a>範例
 下列範例組成文件庫類型 (`SecuredTypeWithFields`) 與不安全的欄位，為型別 (`Distributor`)，可以建立程式庫類型的執行個體和錯誤的階段類型的執行個體沒有權限，來建立這些應用程式程式碼可以讀取的執行個體欄位，即使它沒有保護類型的權限。

 下列程式庫程式碼會違反規則。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>範例
 應用程式無法建立執行個體，因為連結要求保護受保護的型別。 下列類別可讓應用程式取得安全類型的執行個體。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>範例
 下列應用程式會說明如何執行，而不需要存取受保護的類型的方法的權限，程式碼可以存取其欄位。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 此範例會產生下列輸出。

 **建立 SecuredTypeWithFields 的執行個體。** 
**安全類型的欄位： 22、 33**
**變更受保護的型別欄位...** 
**快取的物件欄位： 99、 33**
## <a name="related-rules"></a>相關的規則
 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



