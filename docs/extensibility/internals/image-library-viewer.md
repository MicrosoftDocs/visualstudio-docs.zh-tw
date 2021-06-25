---
title: 影像庫檢視器 |Microsoft Docs
description: 瞭解載入和搜尋影像資訊清單的 Visual Studio 影像庫檢視器工具，讓您能夠查看和操作影像屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898706"
---
# <a name="image-library-viewer"></a>影像庫檢視器
Visual Studio 影像庫檢視器工具可以載入和搜尋影像資訊清單，讓使用者以 Visual Studio 的相同方式來操作它們。 使用者可以改變背景、大小、DPI、高對比和其他設定。 此工具也會顯示每個影像資訊清單的載入資訊，並顯示影像資訊清單中每個影像的來源資訊。 此工具適用于：

1. 診斷錯誤

2. 確保在自訂影像資訊清單中正確設定屬性

3. 搜尋 Visual Studio 映射目錄中的影像，讓 Visual Studio 擴充功能可以使用符合 Visual Studio 樣式的影像。

   ![影像庫檢視器主圖](../../extensibility/internals/media/image-library-viewer-hero.png "影像庫檢視器主圖")

   **影像標記**

   簡短) 的影像標記 (或標記是 GUID： ID 組，可唯一識別影像庫中的影像資產或影像清單資產。

   **映射資訊清單檔案**

   映射資訊清單 (. imagemanifest) 檔是定義一組影像資產的 XML 檔案、代表這些資產的名字，以及代表每個資產的真實影像或影像。 影像資訊清單可以針對舊版 UI 支援定義獨立映射或映射清單。 此外，您也可以在資產上或在每個資產背後的個別影像上設定屬性，以變更這些資產的顯示時機和方式。

   **映射資訊清單架構**

   完整的映射資訊清單看起來像這樣：

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbols**

 為了方便閱讀和維護，影像資訊清單可以使用屬性值的符號。 符號的定義方式如下：

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Subelement**|**定義**|
|-|-|
|匯入|匯入指定資訊清單檔的符號，以用於目前的資訊清單中。|
|Guid|符號代表 GUID，而且必須符合 GUID 格式。|
|識別碼|符號表示識別碼，且必須為非負整數。|
|String|符號代表任一字元串值。|

 符號會區分大小寫，並使用 $ (符號名稱) 語法來參考：

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 某些符號會針對所有資訊清單預先定義。 這些可用於或元素的 Uri 屬性 \<Source> \<Import> ，以參考本機電腦上的路徑。

|**符號**|**說明**|
|-|-|
|CommonProgramFiles|% CommonProgramFiles% 環境變數的值|
|LocalAppData|% LocalAppData% 環境變數的值|
|ManifestFolder|包含資訊清單檔案的資料夾|
|>mydocuments|目前使用者的我的檔資料夾的完整路徑|
|ProgramFiles|% ProgramFiles% 環境變數的值|
|系統|Windows\System32 資料夾|
|WinDir|% WinDir% 環境變數的值|

 **映像**

 \<Image>元素會定義可由標記參考的影像。 建立的 GUID 和識別碼會形成映射的標記。 影像的標記在整個映射庫中必須是唯一的。 如果有一個以上的影像具有指定的名字，則建立程式庫時所遇到的第一個映射就是保留的映射。

 它必須包含至少一個來源。 雖然大小中立的來源可提供各種大小的最佳結果，但並不是必要的。 如果服務要求的影像大小未定義于元素中， \<Image> 而且沒有任何大小中立的來源，則服務會選擇最佳的大小特定來源，並將其調整為所要求的大小。

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Attribute**|**定義**|
|-|-|
|Guid|必影像標記的 GUID 部分|
|識別碼|必影像標記的識別碼部分|
|AllowColorInversion|[選擇性，預設值為 true]指出當使用於深色背景時，影像是否可以以程式設計方式反轉。|

 **來源**

 \<Source>元素會定義 (XAML 和 PNG) 的單一影像來源資產。

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Attribute**|**定義**|
|-|-|
|Uri|必URI，定義可從中載入映射的位置。 可以是下列其中一項：<br /><br /> -使用 application:///授權單位的[套件 URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> -絕對元件資源參考<br /><br /> -包含原生資源之檔案的路徑|
|背景|參數指出來源預定要使用的背景內容。<br /><br /> 可以是下列其中一項：<br /><br /> - *Light*：來源可用於淺色背景。<br /><br /> - *深色*：來源可用於深色背景。<br /><br /> - *Systeminformation.highcontrast*：來源可以在高對比模式中的任何背景使用。<br /><br /> - *HighContrastLight*：來源可以在高對比模式中的淺色背景上使用。<br /><br /> -*HighContrastDark*：來源可在高對比模式的深色背景上使用。<br /><br /> 如果省略 **background** 屬性，則可以在任何背景使用來源。<br /><br /> 如果 **背景** 是 *淺色*、 *深色*、 *HighContrastLight* 或 *HighContrastDark*，則不會反轉來源的色彩。 如果省略 **背景** 或設定為 *systeminformation.highcontrast*，則會以影像的 **AllowColorInversion** 屬性來控制來源的色彩反轉。|

 \<Source>元素只能有下列其中一個選擇性子項目：

|**Element**|**屬性 (所有必要的)**|**定義**|
|-|-|-|
|\<Size>|值|來源將用於在裝置單位)  (指定大小的影像。 影像將會是正方形。|
|\<SizeRange>|MinSize、MaxSize|來源會用於從 MinSize 到 MaxSize (在裝置單位) 的影像。 影像將會是正方形。|
|\<Dimensions>|寬度，高度|來源將用於指定的寬度和高度 (在裝置單位) 的影像。|
|\<DimensionRange>|MinWidth、MinHeight、<br /><br /> MaxWidth、MaxHeight|來源將用於從最小寬度/高度到最大寬度/高度 (的影像（以裝置單位) ）。|

 專案 \<Source> 也可以有選擇性的 \<NativeResource> 子項目，它會定義 \<Source> 從原生元件載入，而不是從 managed 元件載入的。

```xml
<NativeResource Type="type" ID="int" />
```

|**Attribute**|**定義**|
|-|-|
|類型|必原生資源的類型，也就是 XAML 或 PNG|
|識別碼|必原生資源的整數識別碼部分|

 **ImageList**

 \<ImageList>元素會定義可在單一區域中傳回的影像集合。 視需要依需求建立區域。

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Attribute**|**定義**|
|-|-|
|Guid|必影像標記的 GUID 部分|
|識別碼|必影像標記的識別碼部分|
|外部|[選擇性，預設為 false]指出影像標記是否參考目前資訊清單中的影像。|

 包含的映射的標記不需要參考目前資訊清單中所定義的映射。 如果在映射庫中找不到包含的影像，則會在其位置使用空白預留位置影像。

## <a name="how-to-use-the-tool"></a>如何使用工具
 **驗證自訂映射資訊清單**

 若要建立自訂資訊清單，建議您使用 ManifestFromResources 工具來自動產生資訊清單。 若要驗證自訂資訊清單，請啟動映射庫檢視器，然後選取 [檔案] > 設定路徑 .。。開啟 [搜尋目錄] 對話方塊。 此工具將使用搜尋目錄來載入影像資訊清單，但它也會使用它來尋找資訊清單中包含影像的 .dll 檔案，因此請務必在此對話方塊中包含資訊清單和 DLL 目錄。

 ![影像庫檢視器搜尋](../../extensibility/internals/media/image-library-viewer-search.png "影像庫檢視器搜尋")

 按一下 **[新增]** 以選取新的搜尋目錄，以搜尋資訊清單及其對應的 dll。 此工具將會記住這些搜尋目錄，並藉由檢查或取消選取目錄來開啟或關閉它們。

 根據預設，此工具會嘗試尋找 Visual Studio 安裝目錄，並將這些目錄新增至搜尋目錄清單。 您可以手動新增工具找不到的目錄。

 載入所有資訊清單之後，就可以使用此工具來切換影像的 **背景** 色彩、 **DPI**、 **高對比** 或 **grayscaling** ，讓使用者能夠以視覺化方式檢查影像資產，以確認它們是否針對各種設定正確轉譯。

 ![影像庫檢視器背景](../../extensibility/internals/media/image-library-viewer-background.png "影像庫檢視器背景")

 背景色彩可以設定為淺色、深色或自訂值。 選取 [自訂色彩] 會開啟色彩選取對話方塊，並將該自訂色彩新增至 [背景] 下拉式方塊的底部，方便您稍後重新叫用。

 ![影像庫檢視器自訂色彩](../../extensibility/internals/media/image-library-viewer-custom-color.png "影像庫檢視器自訂色彩")

 選取影像的 [標記] 會在右側的 [影像詳細資料] 窗格中，顯示該標記背後每個實際影像的資訊。 此窗格也可讓使用者依名稱或原始 GUID： ID 值複製名字標記。

 ![影像庫檢視器影像的詳細資料](../../extensibility/internals/media/image-library-viewer-image-details.png "影像庫檢視器影像的詳細資料")

 針對每個影像來源顯示的資訊會包含要在其中顯示的背景類型、是否可以主題或支援高對比、其適用於何種大小，或其是否為大小中性，以及影像是否來自原生元件。

 ![影像庫檢視器 Can 佈景主題](../../extensibility/internals/media/image-library-viewer-can-theme.png "影像庫檢視器 Can 佈景主題")

 驗證映射資訊清單時，建議您在其真實世界位置部署資訊清單和映射 DLL。 這會確認任何相對路徑是否正常運作，以及影像庫是否可以找到並載入資訊清單和映射 DLL。

 **搜尋映射目錄 KnownMonikers**

 為了更妥善符合 Visual Studio 樣式，Visual Studio 擴充功能可以使用 Visual Studio 映射目錄中的影像，而不是建立和使用它自己的映射。 這樣做的優點是不需要維護這些映射，並保證映射會有高 DPI 的支援映射，因此它應該會在 Visual Studio 支援的所有 DPI 設定中看起來正確。

 影像庫檢視器允許搜尋資訊清單，讓使用者可以找到代表影像資產的標記，並在程式碼中使用該標記。 若要搜尋影像，請在 [搜尋] 方塊中輸入所需的搜尋字詞，然後按 Enter 鍵。 底部的狀態列會顯示從所有資訊清單中的總影像中找到的相符專案數。

 ![影像庫檢視器篩選器](../../extensibility/internals/media/image-library-viewer-filter.png "影像庫檢視器篩選器")

 在現有的資訊清單中搜尋影像標記時，建議您只搜尋並使用 Visual Studio 映射目錄的名字、其他刻意公開存取的名字，或您自己的自訂的名字標記。 如果您使用非公用的標記，自訂 UI 可能會損毀，或以非預期的方式變更其影像（如果或未變更或更新這些非公用的名字和影像）。

 此外，也可以依 GUID 搜尋。 這種類型的搜尋適用于將清單篩選到單一資訊清單，或資訊清單中包含多個 Guid 的單一子區段。

 ![影像庫檢視器篩選 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "影像庫檢視器篩選 GUID")

 最後，也可以依識別碼進行搜尋。

 ![影像庫檢視器篩選識別碼](../../extensibility/internals/media/image-library-viewer-filter-id.png "影像庫檢視器篩選識別碼")

## <a name="notes"></a>備註

- 根據預設，此工具將會提取 Visual Studio 安裝目錄中出現的數個映射資訊清單。 只有一個可公開取用的標記是 **VisualStudio. ImageCatalog** 資訊清單。 GUID： ae27a6b0-e345-4288-96df-5eaf394ee369 (不 **會** 在自訂資訊清單中覆寫此 GUID) 類型： KnownMonikers

- 此工具會在啟動時嘗試載入其找到的所有影像資訊清單，因此可能需要幾秒鐘的時間，應用程式才會實際出現。 載入資訊清單時，也可能很慢或沒有回應。

## <a name="sample-output"></a>範例輸出
 此工具不會產生任何輸出。
