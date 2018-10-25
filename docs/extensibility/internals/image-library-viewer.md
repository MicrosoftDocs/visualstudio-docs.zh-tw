---
title: 影像庫檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7808c4485a00c080a8a5b260a6472d81bfb7fd44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816821"
---
# <a name="image-library-viewer"></a>影像庫檢視器
Visual Studio 影像庫檢視器工具可以載入，並搜尋映像資訊清單，讓使用者能夠操作這些 Visual Studio 會的方式相同。 使用者可以改變背景、 大小、 DPI、 高對比和其他設定。 此工具也會顯示每個映像資訊清單的載入資訊，並會顯示映像資訊清單中的每個映像的來源資訊。 這項工具可用於：  
  
1. 診斷錯誤  
  
2. 確保屬性已正確設定，在自訂映像資訊清單中  
  
3. 搜尋 Visual Studio 映像目錄中的映像，好讓 Visual Studio 擴充功能可以使用符合的 Visual Studio 樣式的映像  
  
   ![影像庫檢視器 Hero](../../extensibility/internals/media/image-library-viewer-hero.png "影像庫檢視器主圖")  
  
   **影像 moniker**  
  
   影像 moniker （或簡稱 moniker） 是可唯一識別影像資產或映像庫中的影像清單資產的 guid: id 配對。  
  
   **影像資訊清單檔**  
  
   映像資訊清單 (.imagemanifest) 檔案是 XML 檔案會定義一組影像資產，代表這些資產，以及實際的映像或代表每個資產的映像的 moniker。 映像資訊清單可以定義獨立映像或映像會列出舊版的 UI 支援。 此外，也可以變更何時及如何顯示這些資產設定資產上或個別的映像，之後每個資產上的屬性。  
  
   **映像資訊清單結構描述**  
  
   完成映像資訊清單看起來像這樣：  
  
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
  
 **符號**  
  
 當可讀性及維護的協助，映像資訊清單可用於屬性值的符號。 符號定義如下：  
  
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
|**子元素**|**定義**|  
|匯入|匯入使用目前的資訊清單中的指定資訊清單檔案的符號。|  
|Guid|符號表示的 GUID，且必須符合 GUID 格式。|  
|識別碼|符號代表的識別碼，且必須為非負整數。|  
|String|符號代表任意字串值。|  
  
 符號會區分大小寫，且參考使用 $(symbol-name) 語法：  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 所有的資訊清單已預先定義一些符號。 這些可用的 Uri 屬性中\<來源 > 或\<匯入 >，在本機電腦上的參考路徑的項目。  
  
|||  
|-|-|  
|**符號**|**描述**|  
|CommonProgramFiles|%Commonprogramfiles%環境變數的值|  
|LocalAppData|%Localappdata%環境變數的值|  
|ManifestFolder|包含資訊清單檔案的資料夾|  
|MyDocuments|目前使用者的 [我的文件] 資料夾的完整路徑|  
|ProgramFiles|%Programfiles%環境變數的值|  
|系統|Windows\System32 資料夾|  
|WinDir|%Windir%環境變數的值|  
  
 **影像**  
  
 \<映像 > 項目定義的映像，您可以參考 moniker。 GUID 和 ID 結合在一起形成影像 moniker。 跨整個映像庫，影像 moniker 必須是唯一的。 如果多個映像具有指定的 moniker，在建置程式庫時所遇到的第一個是會保留。  
  
 它必須包含至少一個來源。 雖然中性大小來源會提供最佳的結果，跨各種大小，但是它們並非必要項。 如果此服務會要求中未定義大小的影像\<映像 > 項目並沒有中性大小來源，會選擇最佳的特定大小的來源服務，並將其調整為要求的大小。  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|Guid|[必要]影像 moniker GUID 部分|  
|識別碼|[必要]影像 moniker 識別碼部分|  
|AllowColorInversion|[選擇性的預設為 true]指出影像是否可以使用深色背景時以程式設計的方式已反轉其色彩。|  
  
 **來源**  
  
 \<來源 > 項目會定義單一映像來源資產 （XAML 和 PNG）。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|URI|[必要]定義從何處可以載入映像的 URI。 它可以是下列其中一項：<br /><br /> -A [Pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)使用應用程式: / / 授權單位<br /><br /> -絕對元件資源參考<br /><br /> -包含原生資源的檔案路徑|  
|背景|[選用]指出哪些類型的來源要使用的背景。<br /><br /> 它可以是下列其中一項：<br /><br /> - *Light*： 淺色背景上可用的來源。<br /><br /> - *深色*: 來源可以使用深色背景上。<br /><br /> - *高對比*: 來源可以使用高對比模式中的任何背景上。<br /><br /> - *HighContrastLight*： 淺色背景高對比模式中使用的來源。<br /><br /> -*HighContrastDark*： 來源可用在高對比模式中使用深色背景上。<br /><br /> 如果**背景**省略屬性、 來源可以使用任何背景上。<br /><br /> 如果**背景**是*Light*，*深色*， *HighContrastLight*，或*HighContrastDark*，永遠不會反轉來源的色彩。 如果**背景**被省略或設為*高對比*，反轉的來源的色彩由映像的控制**AllowColorInversion**屬性。|  
  
 A\<來源 > 項目可以有一個下列的選擇性子項目：  
  
||||  
|-|-|-|  
|**目**|**屬性 （全部所需）**|**定義**|  
|\<大小 >|值|來源會使用指定的大小 （以裝置為單位） 的映像。 映像會正方形。|  
|\<SizeRange >|MinSize、 MaxSize|來源將使用的映像從 MinSize 至大小上限 （以裝置為單位） （含）。 映像會正方形。|  
|\<維度 >|寬度高度|來源將使用指定的寬度和高度 （以裝置為單位） 的映像。|  
|\<DimensionRange >|MinWidth 或 MinHeight<br /><br /> MaxWidth MaxHeight|來源將用於從最小寬度/高度的映像，以最大寬度/高度 （以裝置為單位） （含）。|  
  
 A\<來源 > 項目也可以選擇性\<NativeResource > 子元素，定義\<來源 > 從原生組件，而不是 managed 組件載入的。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|類型|[必要]資源類型的原生、 XAML 或 PNG|  
|識別碼|[必要]原生資源的整數識別碼部分|  
  
 **ImageList**  
  
 \<ImageList > 項目會定義可傳回單一區域中的映像的集合。 視需求為基礎，帶。  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**屬性**|**定義**|  
|Guid|[必要]影像 moniker GUID 部分|  
|識別碼|[必要]影像 moniker 識別碼部分|  
|外部|[選擇性的預設為 false]指出是否影像 moniker 參考目前的資訊清單中的映像。|  
  
 參考目前的資訊清單中定義的映像沒有包含映像的 moniker。 如果映像庫中找不到包含映像，其位置中都將使用的空白預留位置映像。  
  
## <a name="how-to-use-the-tool"></a>如何使用工具  
 **驗證的自訂映像資訊清單**  
  
 若要建立自訂的資訊清單，我們建議您使用 ManifestFromResources 工具，來自動產生資訊清單。 若要驗證的自訂資訊清單，請在啟動影像庫檢視器，然後選取 檔案 > 設定路徑 以開啟搜尋目錄 對話方塊。 此工具會載入映像資訊清單中，使用搜尋目錄，但它也會使用它以尋找包含在資訊清單中的映像的.dll 檔因此請務必在這個對話方塊包含的資訊清單 」 和 「 DLL 的目錄。  
  
 ![影像庫檢視器搜尋](../../extensibility/internals/media/image-library-viewer-search.png "影像庫檢視器搜尋")  
  
 按一下 **加入...** 選取新的搜尋目錄，若要搜尋的資訊清單和其相對應的 Dll。 此工具會記住這些搜尋目錄，他們可以開啟或關閉核取或取消核取 目錄。  
  
 根據預設，此工具會嘗試尋找 Visual Studio 安裝目錄，並將這些目錄加入至搜尋目錄清單。 您可以手動新增找不到此工具的目錄。  
  
 此工具的所有資訊清單會載入之後，可以用來切換**背景**色彩**DPI**，**高對比**，或**grayscaling**的映像，讓使用者可以視覺化方式檢查以確認它們會呈現正確的各種設定的影像資產。  
  
 ![影像庫檢視器背景](../../extensibility/internals/media/image-library-viewer-background.png "影像庫檢視器背景")  
  
 Light、 暗色調，或自訂值，可以設定的背景色彩。 選取 自訂色彩 會開啟色彩選擇 對話方塊，並將該自訂色彩新增至背景下拉式方塊，供日後辨識稍後底部。  
  
 ![影像庫檢視器自訂色彩](../../extensibility/internals/media/image-library-viewer-custom-color.png "影像庫檢視器自訂色彩")  
  
 選取影像 moniker 右邊的 [映像詳細資料] 窗格中顯示每個實際的映像，該 moniker 背後的資訊。 [] 窗格也可讓使用者名稱或原始 guid: id 值，請將複製的 moniker。  
  
 ![影像庫檢視器映像詳細資料](../../extensibility/internals/media/image-library-viewer-image-details.png "影像庫檢視器映像詳細資料")  
  
 顯示每個映像來源的資訊包含何種背景以顯示上，是否配置其佈景主題，或支援高對比，是有效的何種大小或是否為中性大小，以及映像是否來自原生組件。  
  
 ![影像庫檢視器 Can 佈景主題](../../extensibility/internals/media/image-library-viewer-can-theme.png "影像庫檢視器 Can 佈景主題")  
  
 當驗證的影像清單時，我們建議您部署資訊清單和映像在它們的實際位置的 DLL。 這會驗證任何相對的路徑會正常運作，以及映像庫能找到並載入資訊清單和映像 DLL。  
  
 **搜尋映像目錄 KnownMonikers**  
  
 若要使其更符合 Visual Studio 樣式，Visual Studio 擴充功能可以使用 Visual Studio 映像目錄而不是建立及使用它自己的映像。 這做的優點是不必維護這些映像，並保證映像將會有高 DPI 支援映像，因此看起來應該會在所有 Visual Studio 支援的 DPI 設定正確。  
  
 影像庫檢視器可讓資訊清單，以搜尋，讓使用者能夠尋找表示的影像資產的 moniker，並在程式碼中使用的 moniker。 若要搜尋映像，在搜尋方塊中輸入所需的搜尋字詞，然後按 Enter。 在底部的 [狀態] 列會顯示多少相符項目中找不到映像總計超出所有資訊清單。  
  
 ![影像庫檢視器篩選](../../extensibility/internals/media/image-library-viewer-filter.png "影像庫檢視器篩選")  
  
 搜尋的現有資訊清單中的影像 moniker 時，我們建議您搜尋，並使用只有 Visual Studio 映像的目錄 moniker、 其他刻意可公開存取的 moniker 或您自己自訂的 moniker。 如果您使用非公用的 moniker，自訂的 UI 可能會損毀，或其映像中已經變更非預期的方式還是時變更或更新非公用的 moniker 和影像者除外。  
  
 此外，搜尋由 GUID 是可能的。 這種搜尋適合用來將單一的資訊清單，清單中向下篩選，或如果該資訊清單的資訊清單的單一子區段會包含多個 Guid。  
  
 ![影像庫檢視器篩選 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "影像庫檢視器篩選 GUID")  
  
 最後，依識別碼搜尋可能也是。  
  
 ![影像庫檢視器篩選識別碼](../../extensibility/internals/media/image-library-viewer-filter-id.png "影像庫檢視器篩選識別碼")  
  
## <a name="notes"></a>注意  
  
-   根據預設，此工具會在數個 Visual Studio 安裝目錄中的映像資訊清單中提取。 只有一種具有公開可取用的 moniker 是**Microsoft.VisualStudio.ImageCatalog**資訊清單。 GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (請勿**不**覆寫此自訂資訊清單中的 GUID) 型別： KnownMonikers  
  
-   此工具會嘗試啟動時載入所有影像資訊清單，找到，因此它可能需要花費數秒鐘的時間來實際顯示應用程式。 載入資訊清單時，它可能也會變慢或無回應。  
  
## <a name="sample-output"></a>範例輸出  
 此工具不會產生任何輸出。