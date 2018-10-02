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
ms.openlocfilehash: 900abe516ebd07cf5a8849f269f915623500731e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859701"
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
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 變更預設安全性系統的行為執行 unmanaged 程式碼使用 COM interop 或平台叫用的成員。 一般而言，系統會發出[資料與模型化](/dotnet/framework/data/index)unmanaged 程式碼權限。 此需求就會發生在執行階段的成員，每個引動過程，並檢查權限的呼叫堆疊中的每個呼叫端。 屬性存在時，系統便會發出[連結要求](/dotnet/framework/misc/link-demands)權限： 呼叫端是 JIT 編譯時，系統會檢查立即呼叫端的權限。

 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。 如果您將屬性放在呼叫原生方法的公用成員上時，在呼叫堆疊 （非立即呼叫端） 的呼叫端不需要執行 unmanaged 程式碼的 unmanaged 程式碼權限。 根據公用成員的動作和輸入的處理，它可能會允許不受信任的呼叫端來存取一般限制為可信任的程式碼的功能。

 .NET Framework 依賴安全性檢查，以防止呼叫端目前的處理序位址空間直接存取。 因為這個屬性會略過正常的安全性，您的程式碼會造成嚴重的威脅，如果它可以用來讀取或寫入至處理序的記憶體。 請注意，風險不限於方法，刻意提供存取權來處理記憶體中;它也是出現在任何情況下，其中惡意程式碼能夠存取的任務，比方說，藉由提供令人驚訝、 格式不正確，或無效的輸入。

 預設的安全性原則不授與 unmanaged 程式碼的權限的組件除非它從本機電腦執行或的下列群組的成員：

- 我的電腦區域的程式碼群組

- Microsoft 強式名稱的程式碼群組

- ECMA 強式名稱的程式碼群組

## <a name="how-to-fix-violations"></a>如何修正違規
 請仔細檢閱您的程式碼，以確保這個屬性是絕對必要。 如果您不熟悉使用 managed 程式碼的安全性，或不了解使用這個屬性的安全性含意，請從您的程式碼中移除。 如果屬性是必要的您必須確定呼叫端不能遭到惡意使用您的程式碼。 如果您的程式碼並沒有執行 unmanaged 程式碼的權限，則這個屬性沒有任何作用，而且應該移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的程式碼不提供呼叫端的原生的作業或可以用於破壞性方式的資源的存取。

## <a name="example-1"></a>範例 1
 下面範例違反此規則。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>範例 2
 在下列範例中，`DoWork`方法提供的平台叫用方法的可公開存取的程式碼路徑`FormatHardDisk`。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>範例 3
 在下列範例中，公用方法`DoDangerousThing`造成違規。 若要解決此違規情形，`DoDangerousThing`應該設定成私用，而且其存取權應該透過公用方法受到安全性要求，如下圖所示`DoWork`方法。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [資料與模型化](/dotnet/framework/data/index)
- [連結要求](/dotnet/framework/misc/link-demands)