---
title: CA2118：必須檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3eeff4eca5bcc6d2490fc077501726e3ba7e8de1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917172"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118：必須檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法
|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型或成員具有<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 執行使用 COM interop 或平台引動過程的 unmanaged 程式碼的成員，變更系統的預設安全性行為。 一般而言，系統會進行[資料與模型化](/dotnet/framework/data/index)unmanaged 程式碼權限。 此要求會在每次叫用的成員，執行階段，並且檢查權限的呼叫堆疊中每個呼叫端。 當屬性存在時，系統會進行[連結要求](/dotnet/framework/misc/link-demands)權限： 當呼叫端是 JIT 編譯時，會檢查立即呼叫者的權限。

 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。 如果您將屬性放在呼叫原生方法的公用成員上，呼叫端 （非直接呼叫端） 的呼叫堆疊中不需要執行 unmanaged 程式碼的 unmanaged 程式碼權限。 根據 public 成員的動作和輸入的處理，它可能會允許存取功能的一般限制為可信任的程式碼不受信任呼叫端。

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]依賴安全性檢查，以防止呼叫端直接存取目前的處理序位址空間。 這個屬性會略過標準安全性，因為它可以用來讀取或寫入處理序的記憶體，如果您的程式碼會造成嚴重威脅。 請注意，風險不限於刻意提供存取處理序記憶體; 方法此外也會出現在任何情況下，其中惡意程式碼可以達成存取透過任何方式，例如，藉由提供令人意外、 格式錯誤或無效的輸入。

 預設的安全性原則不會不 unmanaged 程式碼權限授與組件除非從本機電腦正在執行，或屬於下列群組的其中一個：

-   我的電腦區域的程式碼群組

-   Microsoft 強式名稱程式碼群組

-   ECMA 強式名稱程式碼群組

## <a name="how-to-fix-violations"></a>如何修正違規
 請仔細檢閱您的程式碼，以確保此屬性是絕對必要。 如果您不熟悉使用 managed 程式碼安全性或不了解使用此屬性的安全性含意，請從您的程式碼中移除。 如果屬性是必要的您必須確定呼叫端不能遭到惡意使用您的程式碼。 如果您的程式碼並沒有執行 unmanaged 程式碼的權限，此屬性無效，且應移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的程式碼不提供呼叫者存取原生作業或可以用於破壞性方式的資源。

## <a name="example"></a>範例
 下面範例違反此規則。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example"></a>範例
 在下列範例中，`DoWork`方法提供平台叫用方法的可公開存取的程式碼路徑`FormatHardDisk`。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example"></a>範例
 在下列範例中，公用方法`DoDangerousThing`造成違規。 若要解決違規，`DoDangerousThing`應該設定成私用，而且其存取權應該透過公用方法受到安全性要求，如下所示`DoWork`方法。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>另請參閱
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [安全編碼方針](/dotnet/standard/security/secure-coding-guidelines)[資料與模型化](/dotnet/framework/data/index)[連結要求](/dotnet/framework/misc/link-demands)
