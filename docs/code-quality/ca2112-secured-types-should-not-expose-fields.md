---
title: CA2112：受保護類型不應公開欄位
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9784ec48193ae580d7ed41cb745f0befb1f1fde9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915244"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112：受保護類型不應公開欄位
|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型包含公用欄位，而且受到[連結要求](/dotnet/framework/misc/link-demands)。

## <a name="rule-description"></a>規則描述
 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，讓非公用欄位和加入公用屬性或方法傳回的欄位資料。 在類型上的 LinkDemand 安全性檢查保護類型的屬性和方法的存取權。 不過，程式碼存取安全性並不會套用至欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全性問題和良好的設計，您應藉由公用欄位 nonpublic 修復違規。 如果欄位不會儲存資訊應該保持安全，您可以隱藏此規則的警告，您不會依賴欄位的內容。

## <a name="example"></a>範例
 下列範例由程式庫類型所組成 (`SecuredTypeWithFields`) 不安全的欄位，型別 (`Distributor`)，可以建立程式庫類型的執行個體和誤用了的傳遞至類型的執行個體沒有權限來建立它們，而且應用程式程式碼的可以讀取執行個體欄位，即使它沒有權限，可保護類型。

 下列程式庫程式碼違反此規則。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example"></a>範例
 應用程式無法建立執行個體，因為連結要求保護受保護的型別。 下列類別可讓應用程式取得安全類型的執行個體。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example"></a>範例
 下列應用程式會說明如何，沒有權限來存取安全的類型的方法，程式碼可以存取其欄位。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

 此範例會產生下列輸出。

 **建立 SecuredTypeWithFields 的執行個體。** 
 **Secured 類型欄位： 22、 33**
**變更受保護的型別欄位...** 
**快取物件欄位： 99、 33**
## <a name="related-rules"></a>相關的規則
 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](/dotnet/framework/misc/link-demands)[資料與模型化](/dotnet/framework/data/index)