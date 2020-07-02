---
title: 影像庫檢視器 |Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6423c569fd1909539de9460ab3dcde0bcf753c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532024"
---
# <a name="image-library-viewer"></a>影像庫檢視器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 的影像庫檢視器工具可以載入及搜尋影像資訊清單，讓使用者能夠以相同的方式操作，Visual Studio 會這麼做。 使用者可以改變背景、大小、DPI、高對比及其他設定。 此工具也會顯示每個映射資訊清單的載入資訊，並在映射資訊清單中顯示每個影像的來源資訊。 此工具適用于：  
  
1. 診斷錯誤  
  
2. 確保在自訂映射資訊清單中正確設定屬性  
  
3. 搜尋 Visual Studio 映射目錄中的影像，讓 Visual Studio 延伸模組可以使用符合樣式的影像 Visual Studio  
  
   ![影像庫檢視器主圖](../../extensibility/internals/media/image-library-viewer-hero.png "影像庫檢視器主圖")  
  
   **影像標記**  
  
   影像標記（簡稱為名字）是 GUID： ID 組，可唯一識別影像庫中的影像資產或影像清單資產。  
  
   **映射資訊清單檔案**  
  
   影像資訊清單（. imagemanifest）檔案是定義一組影像資產的 XML 檔案、代表這些資產的名字，以及代表每個資產的真實影像或影像。 映射資訊清單可以定義獨立映射或舊版 UI 支援的影像清單。 此外，您可以在資產上，或在每個資產背後的個別影像上設定一些屬性，以變更這些資產的顯示時間和方式。  
  
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
  
 **符號**  
  
 為方便閱讀和維護，映射資訊清單可以使用符號做為屬性值。 符號的定義如下：  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|**Subelement**|**[定義]**|  
|-|-|  
|匯入|匯入指定資訊清單檔的符號，以用於目前的資訊清單。|  
|Guid|符號代表 GUID，且必須符合 GUID 格式。|  
|ID|符號代表識別碼，而且必須是非負整數。|  
|String|符號代表任一字元串值。|  
  
 符號會區分大小寫，並使用 $ （符號-名稱）語法來參考：  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 所有資訊清單都有預先定義的符號。 這些可以用在或元素的 Uri 屬性中 \<Source> \<Import> ，以參考本機電腦上的路徑。  
  
|**符號**|**描述**|  
|-|-|  
|CommonProgramFiles|% CommonProgramFiles% 環境變數的值|  
|LocalAppData|% LocalAppData% 環境變數的值|  
|ManifestFolder|包含資訊清單檔案的資料夾|  
|MyDocuments|目前使用者的 [我的文件] 資料夾的完整路徑|  
|ProgramFiles|% ProgramFiles% 環境變數的值|  
|系統|Windows\System32 資料夾|  
|WinDir|% WinDir% 環境變數的值|  
  
 **映像**  
  
 \<Image>元素會定義可由標記所參考的影像。 同時採用的 GUID 和識別碼會形成影像標記。 影像的標記在整個影像庫中必須是唯一的。 如果有一個以上的映射具有指定的名字，則在建立程式庫時所遇到的第一個影像就是保留的一個。  
  
 它至少必須包含一個來源。 雖然大小中立的來源會提供各種大小的最佳結果，但並不是必要的。 如果要求服務的影像大小未定義于元素中， \<Image> 而且沒有任何大小中立的來源，則服務會選擇最佳的大小特定來源，並將其調整為所要求的大小。  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
    
|**屬性**|**[定義]**|  
|-|-|
|Guid|具備影像標記的 GUID 部分|  
|ID|具備影像標記的識別碼部分|  
|AllowColorInversion|[選用，預設值為 true]指出影像在深色背景上使用時，是否可以以程式設計方式反轉其色彩。|  
  
 **Source**  
  
 \<Source>元素會定義單一影像來源資產（XAML 和 PNG）。  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|**屬性**|**[定義]**|  
|-|-|  
|Uri|具備定義可從中載入影像之位置的 URI。 可以是下列其中一項：<br /><br /> -使用 application:///授權單位的[PACK URI](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx)<br /><br /> -絕對元件資源參考<br /><br /> -包含原生資源之檔案的路徑|  
|背景|選擇性表示要使用來源的背景類型。<br /><br /> 可以是下列其中一項：<br /><br /> - *Light*：來源可以在淺色背景上使用。<br /><br /> - *深色*：來源可以用於深色背景上。<br /><br /> - *Systeminformation.highcontrast*：來源可用於高對比模式中的任何背景。<br /><br /> - *HighContrastLight*：來源可以在高對比模式的淺背景上使用。<br /><br /> -*HighContrastDark*：來源可以在高對比模式的深色背景上使用。<br /><br /> 如果省略**background**屬性，則可以在任何背景使用來源。<br /><br /> 如果**背景**為*淺*、*暗*、 *HighContrastLight*或*HighContrastDark*，則來源的色彩永遠不會反轉。 如果 [**背景**] 省略或設為*systeminformation.highcontrast*，則來源色彩的反轉是由影像的**AllowColorInversion**屬性所控制。|  
  
 專案 \<Source> 只能有下列其中一個選擇性子項目：  
  
|**元素**|**屬性（全部必要）**|**[定義]**|  
|-|-|-|  
|\<Size>|值|來源將用於指定大小的影像（以裝置為單位）。 影像將會是正方形。|  
|\<SizeRange>|MinSize、MaxSize|來源將用於從 MinSize 到大小上限（裝置單位）的影像。 影像將會是正方形。|  
|\<Dimensions>|寬度，高度|來源將用於指定的寬度和高度（以裝置為單位）的影像。|  
|\<DimensionRange>|MinWidth、MinHeight、<br /><br /> MaxWidth、MaxHeight|來源將用於從最小寬度/高度到所含的最大寬度/高度（以裝置單位）為單位的影像。|  
  
 專案 \<Source> 也可以有選擇性的 \<NativeResource> 子項目，它會定義 \<Source> 從原生元件載入而非 managed 元件的。  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|**屬性**|**[定義]**|  
|-|-|  
|類型|具備原生資源的類型，XAML 或 PNG|  
|ID|具備原生資源的整數識別碼部分|  
  
 **ImageList**  
  
 \<ImageList>元素會定義可在單一帶狀中傳回的影像集合。 視需要依需求建立帶狀。  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|**屬性**|**[定義]**|  
|-|-|  
|Guid|具備影像標記的 GUID 部分|  
|ID|具備影像標記的識別碼部分|  
|外部|[選用，預設值為 false]指出影像標記是否參考目前資訊清單中的影像。|  
  
 所包含之影像的標記不需要參考在目前資訊清單中定義的影像。 如果在影像媒體櫃中找不到包含的影像，則會在其位置中使用空白的預留位置影像。  
  
## <a name="how-to-use-the-tool"></a>如何使用工具  
 **驗證自訂映射資訊清單**  
  
 若要建立自訂資訊清單，建議您使用 ManifestFromResources 工具來自動產生資訊清單。 若要驗證自訂資訊清單，請啟動 [映射庫檢視器]，然後選取 [檔案] > 設定路徑 .。。 以開啟 [搜尋目錄] 對話方塊。 此工具會使用搜尋目錄來載入影像資訊清單，但它也會使用它來尋找包含資訊清單中影像的 .dll 檔案，因此請務必在此對話方塊中同時包含資訊清單和 DLL 目錄。  
  
 ![影像庫檢視器搜尋](../../extensibility/internals/media/image-library-viewer-search.png "影像庫檢視器搜尋")  
  
 按一下 [**新增 ...** ] 若要選取新的搜尋目錄，以搜尋資訊清單及其對應的 Dll。 此工具會記住這些搜尋目錄，而且可以藉由檢查或取消選取目錄來開啟或關閉它們。  
  
 根據預設，此工具會嘗試尋找 Visual Studio 安裝目錄，並將這些目錄新增至 [搜尋目錄] 清單。 您可以手動新增工具找不到的目錄。  
  
 載入所有資訊清單之後，就可以使用此工具來切換影像的**背景**色彩、 **DPI**、**高對比**或**grayscaling** ，讓使用者可以視覺化方式檢查影像資產，以確認其是否已針對各種設定正確轉譯。  
  
 ![影像庫檢視器背景](../../extensibility/internals/media/image-library-viewer-background.png "影像庫檢視器背景")  
  
 背景色彩可以設定為 [淺色]、[深色] 或 [自訂值]。 選取 [自訂色彩] 將會開啟色彩選取對話方塊，並將該自訂色彩新增至 [背景] 下拉式方塊的底部，以便稍後輕鬆地重新叫用。  
  
 ![影像庫檢視器自訂色彩](../../extensibility/internals/media/image-library-viewer-custom-color.png "影像庫檢視器自訂色彩")  
  
 選取影像標記會在右側的 [影像詳細資料] 窗格中，顯示該標記背後每個實際影像的資訊。 此窗格也可讓使用者依名稱或原始 GUID： ID 值複製標記。  
  
 ![影像庫檢視器影像的詳細資料](../../extensibility/internals/media/image-library-viewer-image-details.png "影像庫檢視器影像的詳細資料")  
  
 針對每個影像來源顯示的資訊包括要在哪種背景上顯示它、它是否可以有主題或支援高對比、其有效的大小，或其大小是否為中性，以及影像是否來自原生元件。  
  
 ![影像庫檢視器 Can 佈景主題](../../extensibility/internals/media/image-library-viewer-can-theme.png "影像庫檢視器 Can 佈景主題")  
  
 驗證映射資訊清單時，我們建議您在其真實世界位置部署資訊清單和映射 DLL。 這會驗證任何相對路徑是否正常運作，以及影像庫是否可以尋找並載入資訊清單和映射 DLL。  
  
 **搜尋影像目錄 KnownMonikers**  
  
 為了更符合 Visual Studio 樣式，Visual Studio 延伸模組可以使用 Visual Studio 映射目錄中的影像，而不是建立和使用其本身。 這可讓您不必維護這些映射，並保證映射會有高 DPI 的支援影像，因此它在 Visual Studio 支援的所有 DPI 設定中應該看起來是正確的。  
  
 影像庫檢視器允許搜尋資訊清單，讓使用者可以找到代表影像資產的標記，並在程式碼中使用該標記。 若要搜尋影像，請在搜尋方塊中輸入想要的搜尋字詞，然後按 Enter 鍵。 底部的狀態列會顯示在所有資訊清單的總影像中找到多少相符專案。  
  
 ![影像庫檢視器篩選器](../../extensibility/internals/media/image-library-viewer-filter.png "影像庫檢視器篩選器")  
  
 在現有的資訊清單中搜尋影像標記時，我們建議您只搜尋並使用 Visual Studio 映射目錄的名字、其他刻意公開存取的名字，或您自己的自訂名字。 如果您使用非公用的名字標記，自訂 UI 可能會中斷，或其映射以非預期的方式變更，如果或未變更或更新那些非公用的名字和影像。  
  
 此外，也可以依 GUID 搜尋。 這種類型的搜尋適用于將清單向下篩選到單一資訊清單，或如果資訊清單包含多個 Guid，則可用於資訊清單的單一子區段。  
  
 ![影像庫檢視器篩選 GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "影像庫檢視器篩選 GUID")  
  
 最後，也可以依識別碼搜尋。  
  
 ![影像庫檢視器篩選識別碼](../../extensibility/internals/media/image-library-viewer-filter-id.png "影像庫檢視器篩選識別碼")  
  
## <a name="notes"></a>注意  
  
- 根據預設，此工具會提取 Visual Studio 安裝目錄中的數個映射資訊清單。 唯一具有可公開取用之名字標記的是**VisualStudio. ImageCatalog**資訊清單。 GUID： ae27a6b0-e345-4288-96df-5eaf394ee369 （請勿在自訂資訊清單中**覆寫此**GUID）類型： KnownMonikers  
  
- 此工具會在啟動時嘗試載入它找到的所有影像資訊清單，因此可能需要幾秒鐘的時間，應用程式才會實際出現。 載入資訊清單時，它可能也會變慢或沒有回應。  
  
## <a name="sample-output"></a>範例輸出  
 此工具不會產生任何輸出。
