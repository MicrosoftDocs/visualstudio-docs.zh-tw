---
title: Visual Studio 2022 預覽版中的重大 API 變更
description: 瞭解在將擴充功能遷移至 Visual Studio 2022 Preview 時，會導致現有 VS 延伸模組無法編譯的 API 變更。
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308695"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Visual Studio 2022 中的突破性 API 變更

[!INCLUDE [preview-note](../includes/preview-note.md)]

如果您要將擴充功能遷移至 Visual Studio 2022，此處所列的重大變更可能會影響您。

## <a name="reference-assemblies-no-longer-installed"></a>參考元件已不再安裝

您可能已經參考的許多元件，從 Visual Studio 的安裝目錄解析的 MSBuild 已不再安裝。 您應使用 NuGet 來取得所需的 Visual Studio SDK ref 元件。 如需執行此操作的詳細步驟，請參閱 [現代化專案](update-visual-studio-extension.md#modernize-your-vsix-project) 。

## <a name="removed-apis"></a>已移除 Api

在 Visual Studio 2022 中，已移除許多 Api 做為移動 Visual Studio 的一部分。 已移除的 Api 清單可在 [ [已移除的 Api 清單](removed-api-list.md) ] 頁面上找到。

## <a name="interop-breaking-changes"></a>Interop 的重大變更

我們的許多 Api 在 Visual Studio 2022 中已變更，通常會有簡單的變更，可讓您的程式碼容納這些變更。

為了管理重大變更，我們計畫提供新的機制來散發 interop 元件。 具體而言，在 Visual Studio 2022 和以外的範圍中，我們會提供單一 interop 元件，其中包含許多常見公用 Visual Studio 介面的定義。 該元件包含許多 Visual Studio 介面的 managed 定義，而這些介面會從多個 interop 元件中移除。 新的 interop 元件會透過 `Microsoft.VisualStudio.Interop` NuGet 套件散發。

不過，Visual Studio 主要在原生內容中使用，且具有少量中斷性變更的元件，將會繼續擁有自己的 interop 元件 (例如，偵錯工具元件仍會 VisualStudio.Debugger.Interop.dll，如同今天) 的一樣。 在任何情況下，您可以從應用程式參考元件，就像今天一樣。

這是一項重大變更，也就是在此新方法中使用 Api 的擴充功能，與舊版 interop 元件的 Visual Studio 不相容。

這有幾個非常重要的優點，可讓您更輕鬆地將延伸模組更新為 Visual Studio 2022：

- 任何損毀的 Api 都會變成組建階段錯誤，讓您更容易尋找和修正。
- 您只需要更新程式碼，該程式碼會使用在 Visual Studio 2022 中中斷的 API。
- 您將無法意外使用舊的（現在已中斷） API。

整體來說，這些變更將會為所有使用者產生更穩定的 Visual Studio 版本。 這種方法的主要缺點是，您的 managed 元件無法在 Visual Studio 2019 和 Visual Studio 2022 中執行，而不需針對每個目標 Visual Studio 版本編譯您的程式碼一次。

當您因 Visual Studio 2019 與 Visual Studio 2022 之間的 API 差異而進行編譯錯誤時，您可能會發現下列您所遇到的 API 或模式，並提供如何修正此問題的指引。

### <a name="int-or-uint-where-intptr-is-expected"></a>`int`或 `uint` 預期的位置 `IntPtr`

我們預期這會是一個很常見的錯誤。 為了使 Visual Studio 2022 成為64位進程，我們必須修正某些 interop Api，因為它們會假設指標可符合32位整數，以實際使用指標大小的值。

範例錯誤：

> 引數3：無法從 ' out uint ' 轉換成 ' out System.object '

只要將您的程式碼更新為預期或提供，或 `IntPtr` `UIntPtr` 在何處或 `int` 用來 `uint` 解決中斷的情況。

修正範例：

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>在兩個元件中定義的 interop 類型

當 c # 編譯器報告您所使用的型別在兩個元件中定義的錯誤時，您可能會從 SDK 的 Visual Studio 2019 版本參考元件，而該元件應該不再參考。

範例錯誤：

> 錯誤 CS0433：類型 ' IVsDpiAware ' 同時存在於 ' VisualStudio. Interop，Version = 17.0.0.0，Culture = 中性，PublicKeyToken = b03f5f7f11d50a3a ' 和 '。 VisualStudio，Version = 16.0，Culture = 中性，PublicKeyToken = DesignTime '

請參閱我們的 [參考元件](migrated-assemblies.md) 重新對應表，以查看 Visual Studio 2022 中哪個元件名稱是慣用名稱。
請注意，在上述範例錯誤中所命名的兩個元件，並查看此表格，這 `Microsoft.VisualStudio.Interop` 是新的元件名稱。 然後，此修正將會 `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` 從專案中移除的參考。

在某些情況下，我們會針對包含型別轉寄站的已淘汰元件，提供 Visual Studio 2022 版本的套件。 當您使用此選項時，您可以選擇將套件參考 *升級* 為 Visual Studio 2022 版本，而不是移除它。 型別轉寄站會解決編譯器的錯誤。

請記住，這些參考有時可能會以可轉移的套件參考為依據，因此移除的方式可能會比在專案檔中所做的直接參考更難。 在這種情況下，請確定所有直接封裝參考都使用 Visual Studio 2022 SDK 套件本身。 您可以參考 *project.assets.js* ，找出負責導入已淘汰元件的套件鏈。 將可轉移的套件參考更新為 Visual Studio 2022 版，就如同將它安裝為直接參考一樣簡單。

如果您無法變更相依性樹狀結構 (例如，因為它牽涉到協力廠商相依性) ，您可以將直接封裝參考新增至預先 Visual Studio 2022 封裝，並將 `ExcludeAssets="compile"` 中繼資料加入至該 `PackageReference` 專案以解決編譯器錯誤。 但請記住，使用這項技術時，您的延伸模組可能會保留對預先 Visual Studio 2022 元件的相依性，而且您的延伸模組可能會在執行時間發生問題。

### <a name="missing-reference-to-an-interop-assembly"></a>遺漏 interop 元件的參考

當您參考針對預先 Visual Studio 2022 SDK 編譯的元件時，可能會收到關於遺漏元件參考的錯誤。

範例錯誤：

> 錯誤 CS0012 型別 ' IVsTextViewFilter ' 定義在未參考的元件中。 您必須將參考加入至元件 ' VisualStudio. TextManager，Version = 7.1.40304.0，Culture = 中性，PublicKeyToken = b03f5f7f11d50a3a '

使用 [參考元件](migrated-assemblies.md)重新對應表，您可以確認要求的元件實際上不是您應該參考的元件。

最佳修正方式是將您的相依性更新為針對 Visual Studio 2022 SDK 編譯的版本，如此一來，編譯器就不再要求移除的 interop 元件。

在某些情況下，我們會針對包含型別轉寄站的已淘汰元件，提供 Visual Studio 2022 版本的套件。 當此選項可用時，您可以選擇將套件參考新增至已淘汰封裝的 Visual Studio 2022 版本，讓類型轉寄站可以從編譯器解析錯誤。

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` 遺失

這個介面有兩個定義，在兩個命名空間中。 只有其中一個適用于受控耗用量。

Visual Studio 2019 命名空間 | Visual Studio 2022 命名空間 | 預定用途
--|--|--
VisualStudio. IAsyncServiceProvider | VisualStudio. IAsyncServiceProvider | 受控碼耗用量
VisualStudio. IAsyncServiceProvider。 | VisualStudio. COMAsyncServiceProvider. IAsyncServiceProvider | 僅限低層級 interop

如果您看到有關的錯誤 `IAsyncServiceProvider` ， *可能* 是您使用的是原生程式碼的 (第二個數據列) 。
若是如此，您可以更新為新的命名空間，或切換至更容易管理的介面。

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` 和 `_DTE` 類型轉換失敗

`DTE` 和 `_DTE` 都是介面。 其中一個衍生自另一個。 不過，在 Visual Studio 2022 中，基底和衍生類型會交換。
這會讓特定類型指派或轉換失敗。

這也表示您使用的位置 `new DTE()` ，現在必須使用 `new _DTE()` 。

### <a name="missing-argument-on-a-method-invocation"></a>方法調用缺少引數

有幾個方法不再針對 interop API 中的選擇性參數宣告預設引數。
如果您收到有關 COM interop 呼叫遺失引數的錯誤，且參數呼叫 `object` 類型，則 Visual Studio 2019 INTEROP API 定義的先前預設值可能已存在 `""` ，因此請考慮加入 `""` 做為引數以解決編譯錯誤。

如果不確定預設引數是什麼，請嘗試將您的語言服務內容從 Visual Studio 2022 切換至 Visual Studio 2019，以便取得具有舊版 interop 元件的 Intellisense 以查看預設引數是什麼，然後將它明確地新增至您的程式碼。 針對 Visual Studio 2019 進行編譯時，它將會繼續正常運作，但現在會針對 Visual Studio 2022 進行編譯。

修正範例：

```diff
-process4.Attach2();
+process4.Attach2("");
```
