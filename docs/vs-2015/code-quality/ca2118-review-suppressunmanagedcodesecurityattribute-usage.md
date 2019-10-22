---
title: CA2118：審查 SuppressUnmanagedCodeSecurityAttribute 使用方式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb7404d9add159f182ae44b22444dded1aafca20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658645"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118：必須檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型或成員具有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 會變更使用 COM Interop 或平台叫用執行非受控碼之成員的預設安全性系統行為。 一般而言，系統會為非受控碼許可權建立[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化。 這項需求會在執行時間針對成員的每個調用進行，並檢查呼叫堆疊中的每個呼叫端是否有許可權。 當屬性存在時，系統會對許可權進行[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)：當呼叫端是 JIT 編譯時，會檢查立即呼叫端的許可權。

 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。 如果您將屬性放在呼叫原生方法的公用成員上，則呼叫堆疊中的呼叫端（而非直接呼叫端）不需要非受控程式碼許可權就能執行非受控碼。 視公用成員的動作和輸入處理而定，它可能會允許不受信任的呼叫端存取通常限制為可信任的程式碼的功能。

 @No__t_0 依賴安全性檢查，以防止呼叫者取得目前進程的位址空間的直接存取權。 因為此屬性會略過一般安全性，如果您的程式碼可以用來讀取或寫入進程的記憶體，就會產生嚴重威脅。 請注意，風險並不限於刻意提供處理常式記憶體存取權的方法;它也會出現在任何惡意程式碼可以透過任何方式達成存取的情況，例如，藉由提供意外、格式不正確或不正確輸入。

 預設的安全性原則不會授與元件的非受控碼許可權，除非它是從本機電腦執行，或是屬於下列其中一個群組的成員：

- 我的電腦區域程式碼群組

- Microsoft 強式名稱程式碼群組

- ECMA 強式名稱程式碼群組

## <a name="how-to-fix-violations"></a>如何修正違規
 請仔細檢查您的程式碼，以確保此屬性是絕對必要的。 如果您不熟悉 managed 程式碼安全性，或不了解使用此屬性的安全性含意，請將它從您的程式碼中移除。 如果屬性是必要的，您必須確定呼叫端無法惡意使用您的程式碼。 如果您的程式碼沒有執行非受控碼的許可權，這個屬性就不會有任何作用，應予以移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏這項規則的警告，您必須確定您的程式碼不會提供呼叫端存取原生作業或可在破壞性方式使用的資源。

## <a name="example"></a>範例
 下列範例違反規則。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>範例
 在下列範例中，`DoWork` 方法會提供可公開存取的程式碼路徑給平台叫用方法 `FormatHardDisk`。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>範例
 在下列範例中，公用方法 `DoDangerousThing` 會導致違規。 若要解決此違規，應將 `DoDangerousThing` 設為私用，且其存取權應透過安全性需求所保護的公用方法，如 `DoWork` 方法所示。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>請參閱
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 安全程式[代碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[安全性優化](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0)[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)[連結需求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
