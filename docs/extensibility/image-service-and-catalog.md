---
title: 映射服務和目錄 |Microsoft Docs
description: 本文包含採用 Visual Studio 映射服務和映射目錄的指導方針和最佳作法。
ms.custom: SEO-VS-2020
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4483d73a5e6124006f09d05065b6f75f7a654e47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082123"
---
# <a name="image-service-and-catalog"></a>映射服務和目錄
本逐步指南包含採用 Visual Studio 2015 中引進的 Visual Studio 映射服務和映射目錄的指導方針和最佳作法。

 Visual Studio 2015 中引進的映射服務可讓開發人員取得裝置的最佳影像，以及使用者選擇的主題來顯示影像，包括其顯示內容的正確主題。 採用「映射服務」將有助於消除與資產維護、HDPI 調整和主題相關的主要痛點。

|**今日問題**|**方案**|
|-|-|
|背景色彩混合|內建 Alpha 混色|
|主題 (部分) 的影像|主題中繼資料|
|高對比模式|替代高對比資源|
|針對不同的 DPI 模式需要多個資源|以向量為基礎的回復可選取的資源|
|複製的影像|每個影像的一個識別碼概念|

 為什麼要採用映射服務？

- 一律從 Visual Studio 取得最新的「圖元完美」映射

- 您可以提交並使用您自己的映射

- 當 Windows 加入新的 DPI 縮放比例時，不需要測試您的映射

- 解決您的實施中的舊架構障礙

  使用影像服務之前和之後的 Visual Studio shell 工具列：

  ![影像服務之前及之後](../extensibility/media/image-service-before-and-after.png "影像服務之前及之後")

## <a name="how-it-works"></a>運作方式
 映射服務可以提供適用于任何支援的 UI 架構的點陣圖映射：

- WPF： BitmapSource

- WinForms： System.object. Bitmap

- Win32： HBITMAP

  影像服務流程圖

  ![影像服務流程圖](../extensibility/media/image-service-flow-diagram.png "影像服務流程圖")

  **影像的名字**

  簡短) 的影像標記 (或標記是 GUID/識別碼組，可唯一識別影像庫中的影像資產或影像清單資產。

  **已知的名字**

  包含在 Visual Studio 映射目錄中的影像標記集，可供任何 Visual Studio 元件或延伸模組公開取用。

  **映射資訊清單檔案**

  映射資訊清單 (*. imagemanifest*) 檔是定義一組影像資產的 XML 檔案、代表這些資產的名字，以及代表每個資產的真實影像或影像。 影像資訊清單可以針對舊版 UI 支援定義獨立映射或映射清單。 此外，您也可以在資產上或在每個資產背後的個別影像上設定屬性，以變更這些資產的顯示時機和方式。

  **映射資訊清單架構**

  完整的映射資訊清單看起來像這樣：

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
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
|匯入|匯入指定資訊清單檔的符號，以用於目前的資訊清單|
|Guid|符號代表 GUID，且必須符合 GUID 格式|
|識別碼|符號代表識別碼，且必須為非負整數|
|String|符號代表任一字元串值|

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
|系統|*Windows\System32* 資料夾|
|WinDir|% WinDir% 環境變數的值|

 **影像**

 \<Image>元素會定義可由標記參考的影像。 建立的 GUID 和識別碼會形成映射的標記。 影像的標記在整個映射庫中必須是唯一的。 如果有一個以上的影像具有指定的名字，則建立程式庫時所遇到的第一個映射就是保留的映射。

 它必須包含至少一個來源。 大小中立的來源可提供各種大小的最佳結果，但不是必要的。 如果服務要求的影像大小未定義于元素中， \<Image> 而且沒有任何大小中立的來源，則服務會選擇最佳的大小特定來源，並將其調整為所要求的大小。

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
|Uri|必URI，定義可從中載入映射的位置。 可以是下列其中一項：<br /><br /> -使用 application:///授權單位的[套件 URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />-絕對元件資源參考<br />-包含原生資源之檔案的路徑|
|背景|參數指出來源預定要使用的背景內容。<br /><br /> 可以是下列其中一項：<br /><br /> *Light：* 來源可以在淺背景使用。<br /><br /> *深色：* 來源可以在深色背景上使用。<br /><br /> *Systeminformation.highcontrast：* 來源可以在高對比模式中的任何背景使用。<br /><br /> *HighContrastLight：* 來源可以在高對比模式中的淺色背景上使用。<br /><br /> *HighContrastDark：* 來源可以在高對比模式的深色背景上使用。<br /><br /> 如果省略 Background 屬性，則可以在任何背景使用來源。<br /><br /> 如果背景是 *淺色*、 *深色*、 *HighContrastLight* 或 *HighContrastDark*，則不會反轉來源的色彩。 如果省略背景或設定為 *systeminformation.highcontrast*，則會以影像的 **AllowColorInversion** 屬性來控制來源的色彩反轉。|

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

## <a name="using-the-image-service"></a>使用映射服務

### <a name="first-steps-managed"></a> (受控) 的第一個步驟
 若要使用「映射服務」，您必須將下列部分或所有元件的參考新增至您的專案：

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - 如果您使用內建的映射目錄 **KnownMonikers**，則為必要項。

- *Microsoft.VisualStudio.Imaging.dll*

  - 如果您在 WPF UI 中使用 **CrispImage** 和 **ImageThemingUtilities** ，則為必要項。

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - 如果您使用 **ImageMoniker** 和 **ImageAttributes** 類型，則為必要。

  - **EmbedInteropTypes** 應該設定為 true。

- *VisualStudio. DesignTime。*

  - 如果您使用 **IVsImageService2** 類型，則為必要。

  - **EmbedInteropTypes** 應該設定為 true。

- *Microsoft.VisualStudio.Utilities.dll*

  - 如果您在 WPF UI 中使用 **ImageThemingUtilities ImageBackgroundColor** 的 **BrushToColorConverter** ，則為必要項。

- *VisualStudio \<VSVersion> .。。0*

  - 如果您使用 **IVsUIObject** 類型，則為必要。

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - 如果您使用 WinForms 相關的 UI 協助程式，則為必要。

  - **EmbedInteropTypes** 應該設定為 true

### <a name="first-steps-native"></a> (原生) 的第一個步驟
 若要使用映射服務，您必須在專案中包含下列部分或所有標頭：

- **KnownImageIds。h**

  - 如果您使用內建的映射目錄 **KnownMonikers**，則為必要項，但無法使用 **ImageMoniker** 類型，例如從 **IVsHierarchy GetGuidProperty** 或 **GetProperty** 呼叫傳回值時。

- **KnownMonikers。h**

  - 如果您使用內建的映射目錄 **KnownMonikers**，則為必要項。

- **ImageParameters140。h**

  - 如果您使用 **ImageMoniker** 和 **ImageAttributes** 類型，則為必要。

- **VSShell140。h**

  - 如果您使用 **IVsImageService2** 類型，則為必要。

- **ImageThemingUtilities。h**

  - 如果您無法讓影像服務處理您的主題，則為必要。

  - 如果映射服務可以處理您的影像主題，請不要使用此標頭。

::: moniker range="vs-2017"
- **VSUIDPIHelper。h**

  - 如果您使用 DPI 協助程式取得目前的 DPI，則為必要。

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness。h**

  - 如果您使用 DPI 感知協助程式取得目前的 DPI，則為必要。

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>如何? 撰寫新的 WPF UI？

1. 首先，將上述第一個步驟區段中所需的元件參考新增至您的專案。 您不需要新增所有專案，因此請只新增您需要的參考。  (注意：如果您使用或具有 **色彩** 的存取權，而不是 **筆刷**，則可以略過 **公用程式** 的參考，因為您不需要轉換器。 ) 

2. 選取所需的映射，並取得其標記。 如果您有自己的自訂映射和名字標記，請使用 **KnownMoniker**，或使用您自己的。

3. 將 **CrispImages** 新增至您的 XAML。  (請參閱下列範例。 ) 

4. 在您的 UI 階層中設定 **ImageThemingUtilities ImageBackgroundColor** 屬性。  (這應該設定于已知的背景色彩位置，而不一定是 **CrispImage**。 )  (請參閱下列範例。 ) 

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **如何? 更新現有的 WPF UI？**

 更新現有的 WPF UI 是相當簡單的程式，其中包含三個基本步驟：

1. \<Image>以元素取代 UI 中的所有元素 \<CrispImage> 。

2. 將所有來源屬性變更為「標記」屬性。

    - 如果映射永遠不會變更，而且您使用 **KnownMonikers**，則會將該屬性以靜態方式系結至 **KnownMoniker**。  (請參閱上述範例。 ) 

    - 如果映射永遠不會變更，而您使用自己的自訂映射，則會以靜態方式系結至您自己的標記。

    - 如果映射可以變更，請將 [標記] 屬性系結至在屬性變更時通知的程式碼屬性。

3. 在 UI 階層中的某處，設定 **ImageThemingUtilities ImageBackgroundColor** ，以確保色彩反轉能正常運作。

    - 這可能需要使用 **BrushToColorConverter** 類別。  (請參閱上述範例。 ) 

## <a name="how-do-i-update-win32-ui"></a>如何? 更新 Win32 UI？
 將下列程式碼新增至您的程式碼，並在適當的位置取代映射的原始載入。 視需要切換傳回 HBITMAPs 與 HICONs 和 HIMAGELIST 的值。

 **取得映射服務**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **要求影像**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>如何? 更新 WinForms UI？
 將下列程式碼新增至您的程式碼，並在適當的位置取代映射的原始載入。 切換值以視需要傳回點陣圖與圖示。

 **有用的 using 語句**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **取得映射服務**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **要求影像**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>如何? 在新的工具視窗中使用影像的名字？
 已更新 Visual Studio 2015 的 VSIX 封裝專案範本。 若要建立新的工具視窗，請以滑鼠右鍵按一下 VSIX 專案，然後選取 [**加入**  >  **新專案**] (**Ctrl** + **Shift** + **a**) 。 在專案語言的 [擴充性] 節點底下，選取 [ **自訂工具視窗]**，提供工具視窗的名稱，然後按 [ **加入** ] 按鈕。

 這些是在工具視窗中使用名字標記的主要位置。 遵循各項操作的指示：

1. 當索引標籤夠小 (也在 [ **Ctrl**] 索引標籤視窗切換器) 中使用時，工具視窗索引標籤 +  。

    將這一行新增至衍生自 **ToolWindowPane** 型別的類別的函式：

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. 用來開啟工具視窗的命令。

    在套件的 *.vsct* 檔案中，編輯工具視窗的命令按鈕：

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **如何? 在現有的工具視窗中使用影像的名字？**

   將現有的工具視窗更新為使用影像的名字，與建立新工具視窗的步驟類似。

   這些是在工具視窗中使用名字標記的主要位置。 遵循各項操作的指示：

3. 當索引標籤夠小 (也在 [ **Ctrl**] 索引標籤視窗切換器) 中使用時，工具視窗索引標籤 +  。

   1. 移除這些行 (如果它們存在於衍生自 **ToolWindowPane** 型別的類別的函式中) ：

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. 請參閱「如何? 在新的工具視窗中使用影像名字？」的步驟 #1。 一節。

4. 用來開啟工具視窗的命令。

   - 請參閱「如何? 在新的工具視窗中使用影像名字？」的步驟 #2。 一節。

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>如何? 在 .vsct 檔案中使用影像的名字？
 更新 *.vsct* 檔案，如下列批註程式程式碼所示：

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **如果 .vsct 檔案也需要由舊版 Visual Studio 讀取，該怎麼辦？**

 較舊版本的 Visual Studio 無法辨識 **IconIsMoniker** 命令旗標。 您可以在支援的 Visual Studio 版本上，使用影像服務中的影像，但在舊版 Visual Studio 上繼續使用舊樣式的影像。 若要這樣做，您可以讓 *.vsct* 檔案保持不變 (，因此與舊版的 Visual Studio) 相容，然後建立 CSV (以逗號分隔的值) 檔案，該檔案會從 *.vsct* 檔案的元素中定義的 guid/識別碼組對應 \<Bitmaps> 至映射的標記 guid/識別碼配對。

 對應 CSV 檔案的格式為：

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV 檔案會與封裝一起部署，而它的位置是由 **ProvideMenuResource** 封裝屬性的 **IconMappingFilename** 屬性所指定：

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** 是隱含的 $PackageFolder $ (（如) 上述範例所示），或明確地以環境變數（例如 *@ "% UserProfile% \dir1\dir2\MyMappingFile.csv"*）所定義之目錄為根目錄的絕對路徑。

## <a name="how-do-i-port-a-project-system"></a>如何? 的專案系統埠？
 **如何提供專案的 ImageMonikers**

1. 在專案的 **IVsHierarchy** 上執行 **VSHPROPID_SupportsIconMonikers** ，並傳回 true。

2. 如果原始專案使用 **VSHPROPID_IconMonikerGuid** 和 **VSHPROPID_IconMonikerId** VSHPROPID_OpenFolderIconMonikerGuid， **VSHPROPID_IconMonikerImageList** (如果原始專案使用 **VSHPROPID_IconImgList**) 或 **VSHPROPID_OpenFolderIconMonikerId** **、 (、** **VSHPROPID_IconHandle** **VSHPROPID_OpenFolderIconHandle) 。**

3. 變更圖示原始 VSHPROPIDs 的執行方式，以在擴充點要求時建立「舊版」的圖示。 **IVsImageService2** 提供取得這些圖示所需的功能

   **VB/c # 專案類別的額外需求**

   只有在您偵測到專案是 **最外層** 的類別時，才會執行 **VSHPROPID_SupportsIconMonikers** 。 否則，實際的最外層類別在現實情況下可能不支援影像的名字，而您的基底類別可有效地「隱藏」自訂影像。

   **如何? 在 CPS 中使用影像的名字？**

   在 CPS 中設定自訂映射 (一般專案系統) 可以手動方式或透過專案系統擴充性 SDK 隨附的專案範本來完成。

   **使用專案系統擴充性 SDK**

   依照中的指示，為 [專案類型/專案類型提供自訂圖示](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) ，以自訂您的 CPS 影像。 如需 CPS 的詳細資訊，請參閱[Visual Studio 專案系統](https://github.com/Microsoft/VSProjectSystem)擴充性檔

   **手動使用 ImageMonikers**

4. 在您的專案系統中執行並匯出 **IProjectTreeModifier** 介面。

5. 判斷您想要使用的 **KnownMoniker** 或自訂映射的名字。

6. 在 **ApplyModifications** 方法中，在傳回新的樹狀結構之前，于方法中的某處執行下列動作，類似于下列範例：

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. 如果您要建立新的樹狀結構，您可以將所需的名字組傳入 NewTree 方法來設定自訂影像，類似于下列範例：

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>如何? 從實際影像帶轉換成以標記為基礎的影像區域？
 **我需要支援 HIMAGELISTs**

 如果您想要更新的程式碼已經有現有的影像區，而您想要將其更新為使用映射服務，但您受限於需要以影像清單傳遞的 Api，您仍然可以取得映射服務的優點。 若要建立以標記為基礎的影像區域，請遵循下列步驟，從現有的名字標記建立資訊清單。

1. 執行 **ManifestFromResources** 工具，並將它傳遞至圖像塊。 這會產生帶狀的資訊清單。

   - 建議：提供資訊清單的非預設名稱，以符合其使用方式。

2. 如果您只使用 **KnownMonikers**，請執行下列動作：

   - \<Images>將資訊清單的區段取代為 \<Images/> 。

   - 使用 _ # # ) 移除所有的 subimage 識別碼 (任何識別碼 \<imagestrip name> 。

   - 建議：將 AssetsGuid 符號和影像區域符號重新命名以符合其使用方式。

   - 將每個 **ContainedImage** 的 GUID 取代為 $ (ImageCatalogGuid) ，將每個 **ContainedImage** 的識別碼取代為 $ (\<moniker>) ，然後將 External = "true" 屬性新增至每個 **ContainedImage**

       - \<moniker> 應取代為符合影像的 **KnownMoniker** ，但使用 "KnownMonikers"。 從名稱移除。

   - 將 <匯入資訊清單 = "$ (ManifestFolder) \\<相對安裝目錄路徑到 * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest」/ \*> 到區段頂端 \<Symbols> 。

       - 相對路徑是由安裝程式在資訊清單中定義的部署位置所決定。

3. 執行 **ManifestToCode** 工具以產生包裝函式，讓現有的程式碼具有可用於查詢影像區域之影像服務的標記。

   - 建議：提供包裝函式和命名空間的非預設名稱，以符合其使用方式。

4. 執行所有新增、安裝程式撰寫/部署，以及其他程式碼變更，以使用映射服務和新檔案。

   範例資訊清單，包括內部和外部的影像，以查看它看起來的樣子：

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **我不需要支援 HIMAGELISTs**

1. 判斷與影像區域中的影像相符的 **KnownMonikers** 集合，或針對影像區域中的影像建立您自己的名字標記。

2. 更新您用來取得影像區域中所需索引處之影像的任何對應，以改為使用該名字。

3. 更新您的程式碼，以使用映射服務透過更新的對應來要求名字。  (這可能表示更新至 managed 程式碼的 **CrispImages** ，或從映射服務要求 HBITMAPs 或 HICONs，並針對機器碼進行傳遞。 ) 

## <a name="testing-your-images"></a>測試您的映射
 您可以使用影像庫檢視器工具來測試影像資訊清單，以確定一切都已正確撰寫。 您可以在 [Visual Studio 2015 SDK](visual-studio-sdk.md)中找到此工具。 您可以在 [這裡](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true)找到此工具和其他工具的檔。

## <a name="additional-resources"></a>其他資源

### <a name="samples"></a>範例
 GitHub 上的數個 Visual Studio 範例已更新，以示範如何使用映射服務作為各種 Visual Studio 擴充點的一部分。

 檢查 [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 最新的範例。

### <a name="tooling"></a>Tooling
 建立映射服務的一組支援工具，以協助建立/更新可搭配 Image 服務使用的 UI。 如需每個工具的詳細資訊，請參閱工具隨附的檔。 這些工具組含在 [Visual Studio 2015 SDK](visual-studio-sdk.md)中。

 **ManifestFromResources**

 Manifest from Resources 工具會取得 (PNG 或 XAML) 影像資源的清單，並產生映射資訊清單檔，以搭配使用這些映射與影像服務。

 **ManifestToCode**

 Manifest to Code 工具會取得映射資訊清單檔，並產生包裝函式檔案，以參考程式碼 (c + +、c # 或 VB) 或 *.vsct* 檔案中的資訊清單值。

 **ImageLibraryViewer**

 影像庫檢視器工具可以載入影像資訊清單，並允許使用者以相同方式操作它們，Visual Studio 可確保正確撰寫資訊清單。 使用者可以改變背景、大小、DPI 設定、高對比和其他設定。 它也會顯示載入資訊來尋找資訊清單中的錯誤，並顯示資訊清單中每個影像的來源資訊。

## <a name="faq"></a>常見問題集

- 載入時是否有任何相依性必須包含 \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> ？

  - 在所有 interop Dll 上設定 EmbedInteropTypes = "true"。

- 如何? 使用 my 擴充功能部署映射資訊清單嗎？

  - 將 *imagemanifest* 檔案新增至您的專案。

  - 將 [包含在 VSIX 中] 設定為 True。

- 我正在更新 CPS 專案系統。 **ImageName** 和 **StockIconService** 會發生什麼事？

  - 當 CPS 更新為使用名字標記時，會移除這些物件。 您不再需要呼叫 **StockIconService**，只要使用 CPS 公用程式中的 **ToProjectSystemType ()** 擴充方法，將所需的 **KnownMoniker** 傳遞給方法或屬性即可。 您可以在下面找到從 **ImageName** 到 **KnownMonikers** 的對應：

    |**ImageName**|**KnownMoniker**|
    |-|-|
    |ImageName. OfflineWebApp|KnownImageIds|
    |ImageName. WebReferencesFolder|KnownImageIds|
    |ImageName. OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName. ReferenceFolder|KnownImageIds。參考|
    |ImageName。參考|KnownImageIds。參考|
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName. DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName 資料夾|KnownImageIds.FolderClosed|
    |ImageName. OpenFolder|KnownImageIds.FolderOpened|
    |ImageName. ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName. OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName. ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName. DependentFile|KnownImageIds.GenerateFile|
    |ImageName. MissingFile|KnownImageIds.DocumentWarning|
    |ImageName. WindowsForm|KnownImageIds.WindowsForm|
    |ImageName. WindowsUserControl|KnownImageIds|
    |ImageName. WindowsComponent|KnownImageIds.ComponentFile|
    |ImageName.Xml架構|KnownImageIds.XML架構|
    |ImageName.Xml檔案|KnownImageIds.XML檔案|
    |ImageName. WebForm|KnownImageIds|
    |ImageName|KnownImageIds|
    |ImageName. WebUserControl|KnownImageIds.WebUserControl|
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName. AspPage|KnownImageIds.ASPFile|
    |ImageName. GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName. WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName 樣式表單|KnownImageIds 樣式表單|
    |ImageName. ScriptFile|KnownImageIds.JS腳本|
    |ImageName. TextFile|KnownImageIds.Doc>ument|
    |ImageName. SettingsFile|KnownImageIds 設定|
    |ImageName 資源|KnownImageIds.DocumentGroup|
    |ImageName 點陣圖|KnownImageIds 影像|
    |ImageName 圖示|KnownImageIds.IconFile|
    |ImageName 影像|KnownImageIds 影像|
    |ImageName. ImageMap|KnownImageIds.ImageMapFile|
    |ImageName. XWorld|KnownImageIds.XWorldFile|
    |ImageName 音訊|KnownImageIds 音效|
    |ImageName 影片|KnownImageIds 媒體|
    |ImageName.Cab|KnownImageIds.CAB專案|
    |ImageName .Jar|KnownImageIds.JARFile|
    |ImageName|KnownImageIds DataTable|
    |ImageName. PreviewFile|KnownImageIds 報表|
    |ImageName. DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName. XsltFile|KnownImageIds. XSLTransform|
    |ImageName 資料指標|KnownImageIds.CursorFile|
    |ImageName. AppDesignerFolder|KnownImageIds。屬性|
    |ImageName 資料|KnownImageIds 資料庫|
    |ImageName 應用程式|KnownImageIds 應用程式|
    |ImageName 資料集|KnownImageIds.DatabaseGroup|
    |ImageName .Pfx|KnownImageIds 憑證|
    |ImageName .Snk|KnownImageIds 規則|
    |ImageName. VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName。空白|KnownImageIds。空白|
    |ImageName. MissingFolder|KnownImageIds.FolderOffline|
    |ImageName. SharedImportReference|KnownImageIds.SharedProject|
    |ImageName. SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - 我正在更新完成清單提供者。 哪些 **KnownMonikers** 符合舊的 **StandardGlyphGroup** 和 **StandardGlyph** 值？

    |名稱|名稱|名稱|
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||參考|
    |GlyphLibrary||程式庫|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||對話|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||程式碼片段|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||遞迴|
    |GlyphXmlItem||標籤|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||文件|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||對|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||對|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
