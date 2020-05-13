---
title: 影像庫檢視器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707740"
---
# <a name="image-library-viewer"></a>影像庫檢視器
可視化工作室圖像庫檢視器工具可以載入和搜尋影像清單,允許使用者以視覺工作室相同的方式操作它們。 用戶可以更改背景、大小、DPI、高對比度和其他設置。 該工具還顯示每個圖像清單的載入資訊,並顯示影像清單中每個圖像的來源資訊。 此工具可用於:

1. 診斷錯誤

2. 確保在自訂映像清單中正確設定屬性

3. 在可視化工作室影像目錄中搜尋影像,以便可視化工作室擴展可以使用適合視覺工作室樣式的圖像

   ![影像庫檢視器主圖](../../extensibility/internals/media/image-library-viewer-hero.png "影像庫檢視器主圖")

   **影像名稱**

   圖像名稱物件(簡稱名稱)是 GUID:ID 對,用於唯一標識圖像庫中的圖像資產或圖像清單資產。

   **影像清單檔案**

   圖像清單 (.imagemanifest) 檔案是定義一組圖像資產的 XML 檔、表示這些資產的名號以及表示每個資產的真實圖像或圖像。 映射清單可以為舊版 UI 支援定義獨立映射或圖像清單。 此外,還可以在每個資產後面的單個圖像上設置一些屬性,以更改這些資產的顯示時間以及方式。

   **映射清單架構**

   完整的影像清單如下所示:

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

 作為可讀性和維護輔助工具,圖像清單可以使用符號進行屬性值。 符號定義的以下:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Subelement**|**定義**|
|匯入|匯入給定清單檔的符號,用於當前清單。|
|Guid|符號表示 GUID,必須匹配 GUID 格式。|
|ID|符號表示 ID,並且必須是非負整數。|
|String|符號表示任意字串值。|

 符號區分大小寫,並使用 $(符號名稱)語法引用:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 某些符號是為所有清單預定義的。 這些可用於\<源>的Uri屬性,或者\<導入>元素以引用本地電腦上的路徑。

|||
|-|-|
|**象徵**|**說明**|
|CommonProgramFiles|%公共程式檔案% 環境變數的值|
|本地應用資料|%LocalAppData% 環境變數的值|
|清單資料夾|引入清單檔案的資料夾|
|我的文件|目前使用者的「我的文件」 資料夾的完整路徑|
|ProgramFiles|%程式檔案% 環境變數的值|
|系統|Windows_System32資料夾|
|溫迪爾|%WinDir% 環境變數的值|

 **影像**

 圖像\<>元素定义一个可以由名字对象引用的图像。 GUID 和 ID 一起構成圖像名稱。 圖像的綽號必須在整個圖像庫中是唯一的。 如果多個圖像具有給定的名字物件,則構建庫時遇到的第一個圖像是保留的映射。

 它必須至少包含一個源。 儘管大小中性源將在各種尺寸中提供最佳結果,但它們不是必需的。 如果要求服務提供\<未在 Image> 元素中定義的大小圖像,並且沒有大小無關的源,則服務將選擇最佳特定於大小的源並將其縮放到請求的大小。

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**屬性**|**定義**|
|Guid|[ 必需]影像名稱的 GUID 部份|
|ID|[ 必需]影像名稱物件識別碼部份|
|允許顏色反轉|[選擇可選,預設為 true]指示在深色背景上使用時,圖像的顏色是否可以以程式設計方式反轉。|

 **來源**

 源\<>元素定义单个映像源资产(XAML 和 PNG)。

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**屬性**|**定義**|
|Uri|[ 必需]定義圖像從何處載入的 URI。 可以是下列其中一項：<br /><br /> - 使用application:///許可權的[包URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> - 絕對元件資源參照<br /><br /> - 包含本機資源的檔案路徑|
|背景|[選擇性的]指示源在哪些背景上打算使用。<br /><br /> 可以是下列其中一項：<br /><br /> - *光*:光源可用於光背景。<br /><br /> - *黑暗*:源可用於深色背景。<br /><br /> - *高對比度*:源可用於高對比度模式下的任何背景。<br /><br /> - *高對比度光*:光源可在高對比度模式下在光背景上使用。<br /><br /> -*高對比度暗*:源可用於高對比度模式下的黑暗背景。<br /><br /> 如果省略**了背景**屬性,則源可用於任何背景。<br /><br /> 如果**背景**是 *「淺色*」、*暗*色、*高對比度或**高對比度暗*,則源的顏色永遠不會反轉。 如果「**背景**」省略或設定為 *「高對比度*」,則源顏色的反轉由影像的**AllowColor 反轉**屬性控制。|

 \<來源>元素可以完全具有以下可選子元素之一:

||||
|-|-|-|
|**Element**|**屬性(所有必要)**|**定義**|
|\<大小>|值|源將用於給定大小的圖像(以設備單位為單位)。 圖像將是方形的。|
|\<大小範圍>|最小大小,最大尺寸|源將用於從最小尺寸到 MaxSize(以設備單位為單位)的圖像(包括設備單位)。 圖像將是方形的。|
|\<尺寸>|寬度，高度|源將用於給定寬度和高度(以設備單位為單位)的圖像。|
|\<尺寸範圍>|最小寬度, 最小高度,<br /><br /> 最大寬度,最大高度|源將用於從最小寬度/高度到最大寬度/高度(以設備單位為單位)的圖像(包括設備單位)。|

 \<源>元素還可以具有可選\<的本機資源>子元素,該子元素定義從本機程式集而不是託管程式集載入的\<源>。

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**屬性**|**定義**|
|類型|[ 必需]本機資源的類型,XAML 或 PNG|
|ID|[ 必需]本機資源的整數 ID 部份|

 **圖片清單**

 ImageList \<>元素定义可在单个条带中返回的图像集合。 根據需要,該條條按需構建。

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**屬性**|**定義**|
|Guid|[ 必需]影像名稱的 GUID 部份|
|ID|[ 必需]影像名稱物件識別碼部份|
|外部|[選擇選擇,預設錯誤]指示圖像名字物件是否引用當前清單中的圖像。|

 包含圖像的綽號不必引用在當前清單中定義的圖像。 如果在圖像庫中找不到包含的圖像,則在其位置將使用空白占位符圖像。

## <a name="how-to-use-the-tool"></a>如何使用該工具
 **驗證自訂映像清單**

 要創建自定義清單,我們建議您使用"清單源"工具自動生成清單。 要驗證自訂清單,請啟動映像函式庫檢視器並選擇檔案>設定路徑...以打開「搜索目錄」對話框。 該工具將使用搜尋目錄載入影像清單,但它也會使用它們來尋找包含清單中圖像的.dll檔,因此請確保在此對話框中同時包含清單和 DLL 目錄。

 ![影像庫檢視器搜尋](../../extensibility/internals/media/image-library-viewer-search.png "影像庫檢視器搜尋")

 按下「**添加..."** 以選擇新的搜尋目錄以搜尋清單及其相應的 DLL。 該工具將記住這些搜索目錄,並且可以通過檢查或取消檢查目錄來打開或關閉它們。

 默認情況下,該工具將嘗試查找 Visual Studio 安裝目錄,並將這些目錄添加到搜索目錄清單中。 您可以手動添加工具找不到的目錄。

 載入所有清單後,該工具可用於切換影像**的背景**顏色 **、DPI、****高對比度**或**灰度,** 以便使用者可以直觀地檢查圖像資產,以驗證它們是否正確呈現為各種設置。

 ![影像庫檢視器背景](../../extensibility/internals/media/image-library-viewer-background.png "影像庫檢視器背景")

 背景顏色可以設置為「淺色」、深色或自定義值。 選擇「自訂顏色」將打開顏色選擇對話框,並將自訂顏色添加到背景組合框的底部,以便以後輕鬆呼叫。

 ![影像庫檢視器自訂色彩](../../extensibility/internals/media/image-library-viewer-custom-color.png "影像庫檢視器自訂色彩")

 選擇圖像名字物件會在右側的「圖像詳細資訊」 窗格中顯示該名字物件後面的每個真實圖像的資訊。 該窗格還允許使用者按名稱或原始 GUID:ID 值複製名字物件。

 ![影像庫檢視器影像的詳細資料](../../extensibility/internals/media/image-library-viewer-image-details.png "影像庫檢視器影像的詳細資料")

 為每個圖像源顯示的資訊包括要顯示它的背景類型、是否可以以主題或支援高對比度、它適用於什麼大小或大小是否中性,以及圖像是否來自本機程式集。

 ![影像庫檢視器 Can 佈景主題](../../extensibility/internals/media/image-library-viewer-can-theme.png "影像庫檢視器 Can 佈景主題")

 驗證映射清單時,我們建議您在其實際位置部署清單和映射 DLL。 這將驗證任何相對路徑是否正常工作,以及圖像庫是否可以查找和載入清單和圖像 DLL。

 **搜尋影像目錄 已知莫尼克斯**

 為了更好地匹配 Visual Studio 樣式,Visual Studio 擴展可以使用 Visual Studio 圖像目錄中的圖像,而不是創建和使用自己的圖像。 這樣做的好處是不必維護這些圖像,並且保證圖像具有高 DPI 支援圖像,因此在 Visual Studio 支援的所有 DPI 設置中,圖像看起來應該是正確的。

 圖像庫檢視器允許搜尋清單,以便使用者可以找到表示圖像資產的綽號,並在代碼中使用該名字物件。 要搜索圖像,請在搜尋框中輸入所需的搜索詞,然後按 Enter。 底部的狀態列將顯示從所有清單中的總圖像中找到的匹配項數。

 ![影像庫檢視器篩選器](../../extensibility/internals/media/image-library-viewer-filter.png "影像庫檢視器篩選器")

 在現有清單中搜索圖像名字物件時,我們建議您僅搜索和使用 Visual Studio 圖像目錄的名言、其他有意公開存取的名字,或者您自己的自定義名字。 如果使用非公共名字,如果更改或更新這些非公共名字物件和圖像,自定義 UI 可能會中斷或以意外方式更改其映射。

 此外,還可以通過 GUID 進行搜索。 這種類型的搜索可用於將清單篩選到單個清單,或者如果清單包含多個 GUID,則該清單的單個子節。

 ![影像庫檢視器篩選 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "影像庫檢視器篩選 GUID")

 最後,也可以按 ID 進行搜索。

 ![影像庫檢視器篩選識別碼](../../extensibility/internals/media/image-library-viewer-filter-id.png "影像庫檢視器篩選識別碼")

## <a name="notes"></a>注意

- 默認情況下,該工具將拉取 Visual Studio 安裝目錄中存在的多個圖像清單。 唯一具有公開易用名字的,是**微軟.VisualStudio.Image Catalog**清單。 GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (**不要**在自定義清單中覆蓋此 GUID) 類型: 已知Monikers

- 該工具嘗試啟動以載入它找到的所有映射清單,因此應用程式可能需要幾秒鐘才能實際顯示。 載入清單時,它也可能很慢或無回應。

## <a name="sample-output"></a>範例輸出
 此工具不生成任何輸出。
