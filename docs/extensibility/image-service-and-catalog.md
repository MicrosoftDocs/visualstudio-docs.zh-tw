---
title: 影像服務和目錄 |微軟文件
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710380"
---
# <a name="image-service-and-catalog"></a>影像服務與目錄
本說明書包含採用 Visual Studio 2015 中介紹的可視化工作室影像服務和圖像目錄的指南和最佳實踐。

 Visual Studio 2015 中引入的圖像服務允許開發人員獲得設備的最佳圖像和使用者選擇的主題來顯示圖像,包括正確選擇顯示圖像的上下文。 採用影像服務將有助於消除與資產維護、HDPI 擴展和準備相關的主要痛點。

|||
|-|-|
|**今天的問題**|**方案**|
|背景顏色混合|內置 Alpha 混合|
|人物(一些)影像|主題中繼資料|
|高對比模式|備用高對比度資源|
|需要多種資源用於不同的 DPI 模式|具有基於向量的回退的可選資源|
|重複影像|每個映像概念一個識別子|

 為什麼要採用影像服務?

- 始終從視覺工作室獲取最新的「圖元完美」圖像

- 您可以提交與使用自己的影像

- 當 Windows 新增新的 DPI 縮放時,無需測試映像

- 解決實作中的舊體系結構障礙

  使用影像服務之前和之後的 Visual Studio 外殼工具列:

  ![影像服務之前及之後](../extensibility/media/image-service-before-and-after.png "影像服務之前及之後")

## <a name="how-it-works"></a>運作方式
 影像服務可以提供適合任何受支援的 UI 框架的位映射映射:

- WPF:點陣圖來源

- 贏表單:系統.繪圖.位元圖

- 贏32: HBITMAP

  影像服務流程圖

  ![影像服務流程圖](../extensibility/media/image-service-flow-diagram.png "影像服務流程圖")

  **影像名稱**

  圖像名稱物件(簡稱"名稱")是一個 GUID/ID 對,用於唯一標識圖像庫中的圖像資產或圖像列表資產。

  **已知名字**

  視覺工作室圖像目錄中包含的圖像名字集,任何 Visual Studio 元件或擴展都公開使用。

  **影像清單檔案**

  圖像清單 *(.imagemanifest*) 檔案是定義一組圖像資產的 XML 檔、表示這些資產的名號以及表示每個資產的真實圖像或圖像。 映射清單可以為舊版 UI 支援定義獨立映射或圖像清單。 此外,還可以在每個資產後面的單個圖像上設置一些屬性,以更改這些資產的顯示時間以及方式。

  **映射清單架構**

  完整的影像清單如下所示:

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
|匯入|匯入給定清單檔符號,用於目前的清單|
|Guid|符號表示 GUID 必須符合 GUID 格式|
|ID|符號表示 ID,並且必須是非負整數|
|String|符號表示任意字串值|

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
|系統|*Windows_System32*資料夾|
|溫迪爾|%WinDir% 環境變數的值|

 **影像**

 圖像\<>元素定义一个可以由名字对象引用的图像。 GUID 和 ID 一起構成圖像名稱。 圖像的綽號必須在整個圖像庫中是唯一的。 如果多個圖像具有給定的名字物件,則構建庫時遇到的第一個圖像是保留的映射。

 它必須至少包含一個源。 大小中性源將在各種大小中提供最佳結果,但不是必需的。 如果要求服務提供\<未在 Image> 元素中定義的大小圖像,並且沒有大小無關的源,則服務將選擇最佳特定於大小的源並將其縮放到請求的大小。

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
|Uri|[ 必需]定義圖像從何處載入的 URI。 可以是下列其中一項：<br /><br /> - 使用application:///許可權的[包URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />- 絕對元件資源參照<br />- 包含本機資源的檔案路徑|
|背景|[選擇性的]指示源在哪些背景上打算使用。<br /><br /> 可以是下列其中一項：<br /><br /> *淺色:* 光源可用於淺色背景。<br /><br /> *黑暗:* 源可用於深色背景。<br /><br /> *高對比度:* 源可以在高對比度模式下的任何背景上使用。<br /><br /> *高對比度指示燈:* 光源可在高對比度模式下的光背景上使用。<br /><br /> *高對比度暗:* 源可用於高對比度模式下的黑暗背景。<br /><br /> 如果省略了背景屬性,則源可用於任何背景。<br /><br /> 如果背景是 *「淺色*」、*暗*色、*高對比度或**高對比度暗*,則源的顏色永遠不會反轉。 如果"背景"省略或設置為 *"高對比度*",則源顏色的反轉由圖像的**AllowColor 反轉**屬性控制。|

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

## <a name="using-the-image-service"></a>使用影像服務

### <a name="first-steps-managed"></a>第一步(託管)
 要使用影像服務,您需要加入此專案的檔案或所有程式集的參考:

- *微軟.VisualStudio.ImageCatalog.dll*

  - 需要,如果你使用內置的影像目錄**已知莫尼克器**。

- *微軟.VisualStudio.成像.dll*

  - 如果在 WPF UI 中使用**CrispImage**和**ImageTheming 實用程式**,則需要。

- *微軟.VisualStudio.成像.Interop.14.0.設計時間.dll*

  - 如果使用**ImageMoniker**和**ImageAttributes**類型,則需要。

  - **嵌入類型**應設定為 true。

- *微軟.VisualStudio.shell.Interop.14.0.設計時間*

  - 如果使用**IVImageService2**類型,則需要。

  - **嵌入類型**應設定為 true。

- *微軟.VisualStudio.實用程式.dll*

  - 如果您使用 **「畫筆到顏色轉換器****」進行影像實用程式.圖像背景顏色**,則需要在 WPF UI 中使用。

- *微軟.VisualStudio.Shell.\<vsVersion>.0*

  - 如果使用**IVUIObject**類型,則需要。

- *微軟.VisualStudio.shell.Interop.10.0.dll*

  - 如果使用與 WinForms 相關的 UI 幫助器,則需要。

  - **嵌入類型**應設定為 true

### <a name="first-steps-native"></a>第一步(本機)
 要使用影像服務,您需要向專案包括以下部分或全部標頭:

- **已知影像 Ids.h**

  - 如果使用內置圖像目錄**已知 Monikers**,但無法使用**ImageMoniker**類型,例如從**IV 層次結構 GetGuidProperty**或**GetProperty**調用返回值時,則是必需的。

- **已知莫尼克斯.h**

  - 需要,如果你使用內置的影像目錄**已知莫尼克器**。

- **影像參數140.h**

  - 如果使用**ImageMoniker**和**ImageAttributes**類型,則需要。

- **VSShell140.h**

  - 如果使用**IVImageService2**類型,則需要。

- **圖片實用程式.h**

  - 如果您不能讓影像服務為您處理主名,則需要。

  - 如果影像服務可以處理您的圖像標題,則不要使用此標頭。

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - 如果使用 DPI 説明器獲取當前 DPI,則需要。

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - 如果使用 DPI 意識幫助器獲取當前 DPI,則需要。

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>如何編寫新的 WPF UI?

1. 首先,將上述第一步部分中所需的程式集引用添加到專案中。 您無需添加所有引用,因此只需添加所需的引用。 (注意:如果您正在使用或有權訪問**顏色**而不是**畫筆**,則可以跳過對**實用程式**的引用,因為您不需要轉換器。

2. 選擇所需的圖像並獲取其名字物件。 使用**已知Moniker,** 或者使用你自己的,如果你有自己的自定義圖像和名字。

3. 將**CrispImage**添加到您的 XAML 中。 (請參閱下面的示例。

4. 在 UI 層次結構中設置**ImageTheming 實用程式.Image背景顏色**屬性。 (這應設置在已知背景顏色的位置,不一定在**CrispImage**上。(請參閱下面的示例。

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

 **如何更新現有的 WPF UI?**

 更新現有的 WPF UI 是一個相對簡單的過程,由三個基本步驟組成:

1. 將\<UI 中的所有圖像>\<元素替換為 CrispImage>元素。

2. 將所有源屬性更改為 Moniker 屬性。

    - 如果圖像從未更改,並且您正在使用 **「已知莫尼克器**」,則靜態地將該屬性綁定到**已知 Moniker。** (請參閱上述範例。

    - 如果圖像從未更改,並且您正在使用自己的自定義映射,則靜態綁定到您自己的名字物件。

    - 如果圖像可以更改,則將 Moniker 屬性綁定到代碼屬性,該屬性會通知屬性更改。

3. 在 UI 層次結構的某處,設置**ImageTheming 實用程式.Image背景顏色**,以確保顏色反轉正常工作。

    - 這可能需要使用**BrushtoColor 轉換器**類。 (請參閱上述範例。

## <a name="how-do-i-update-win32-ui"></a>如何更新 Win32 UI?
 在適當的情況下向代碼添加以下內容,以替換映射的原始載入。 根據需要切換用於返回 HBITMA 與 HICOS 與 HIMAGELIST 的值。

 **取得影像服務**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **要求映像**

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

## <a name="how-do-i-update-winforms-ui"></a>如何更新 WinForms UI?
 在適當的情況下向代碼添加以下內容,以替換映射的原始載入。 根據需要切換用於返回位圖和圖示的值。

 **有用的使用敘述**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **取得影像服務**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **要求映像**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>如何在新工具視窗中使用圖像名字物件?
 VSIX 包項目範本已更新為 Visual Studio 2015。 要建立新的工具視窗,請右鍵按一下 VSIX 專案並選擇「**新增新** > **專案**+**Shift**+**」(Ctrl**Shift**A)。** 在專案語言的「可擴充性」節點下,選擇 **「自訂工具視窗**」,為工具視窗指定名稱,然後按 **「添加**」按鈕。

 這些是工具視窗中使用名字器的關鍵位置。 按照每個說明:

1. 當選項卡變得足夠小時工具視窗選項卡(也用於**Ctrl**+**選項卡**視窗切換器)。

    將此行新增到派生自**工具視窗窗格**型態類別的類別的建構函數:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. 打開工具視窗的命令。

    在套件的 *.vsct*檔案中,編輯工具視窗的命令按鈕:

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

   **如何在現有工具視窗中使用圖像名字物件?**

   更新現有工具視窗以使用圖像名字對象類似於創建新工具視窗的步驟。

   這些是工具視窗中使用名字器的關鍵位置。 按照每個說明:

3. 當選項卡變得足夠小時工具視窗選項卡(也用於**Ctrl**+**選項卡**視窗切換器)。

   1. 移除從**工具WindowPane**類型派生的類的建構函數中的這些行(如果存在):

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. #1 請參閱「如何在新工具視窗中使用圖像名字器? 上文部分。

4. 打開工具視窗的命令。

   - 請參閱 #2「如何在新工具視窗中使用圖像名字器? 上文部分。

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>如何在 .vsct 檔案中使用圖像名字物件?
 依以下註解行所示更新 *.vsct*檔案:

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

 **如果我的 .vsct 檔還需要由舊版本的 Visual Studio 讀取,該怎麼辦?**

 較舊版本的 Visual Studio 無法識別**圖示 IsMoniker**命令標誌。 您可以在支援該圖像工作室的 Visual Studio 版本上使用影像服務中的圖像,但在舊版本的 Visual Studio 上繼續使用舊式圖像。 為此,您將保持 *.vsct*檔不變(因此與舊版本的 Visual Studio 相容),並創建一個 CSV(逗號分隔值)檔,該檔從\<*.vsct*檔中 定義的 GUID/ID 對映射到圖像名字物件 GUID/ID 對>元素。

 對應 CSV 檔案格式是:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV 檔案隨包一起部署,其位置由**ProvideMenuResource**套件屬性的**IconMappingFilename**屬性指定:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename**要麼是隱式植根於 $PackageFolder$的相對路徑(如上例所示),或者是一個顯式植根於環境變數定義的目錄(如 *_"%userProfile%%_dir1_dir2_MyMappingFile.csv")* 的絕對路徑。

## <a name="how-do-i-port-a-project-system"></a>如何移植項目系統?
 **如何提供影像Monikers**

1. 在專案的**IV 層次結構**上實施**VSHPROPID_SupportsIconMonikers,** 然後傳回 true。

2. 實施**VSHPROPID_IconMonikerImageList(** 如果原始專案使用**VSHPROPID_IconImgList)****VSHPROPID_IconMonikerGuid**或 VSHPROPID_IconMonikerGuid、VSHPROPID_IconMonikerId、VSHPROPID_OpenFolderIconMonikerGuid、VSHPROPID_OpenFolderIconMonikerId(**VSHPROPID_OpenFolderIconMonikerId**如果原始專案使用**VSHPROPID_IconHandle**和**VSHPROPID_OpenFolderIconHandle)。** **VSHPROPID_IconMonikerId** **VSHPROPID_OpenFolderIconMonikerGuid**

3. 更改圖示的原始 VSHPROPID 的實現,以建立圖示的「舊」版本(如果擴展點請求)。 **IVsImageService2**提供取得這些圖示所需的功能

   **VB/C++ 專案風格的額外要求**

   只有當你檢測到你的專案是最**外在的味道**時,才實現**VSHPROPID_SupportsIconMonikers。** 否則,實際最外在的味道可能不支援圖像名字在現實中,你的基本風味可能有效地"隱藏"自定義圖像。

   **如何在 CPS 中使用圖像名字?**

   在 CPS(通用專案系統)中設置自定義映射可以手動或通過專案系統擴展 SDK 附帶的專案範本進行。

   **使用專案系統擴充性 SDK**

   按照"[為項目類型/專案類型提供自訂圖示](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md)「中的說明進行自訂自訂 CPS 圖像。 有關 CPS 的更多資訊,請參閱[可視化工作室專案系統擴展文檔](https://github.com/Microsoft/VSProjectSystem)

   **手動使用影像 Monikers**

4. 在專案系統中實現並匯出**IProjectTree修改器**介面。

5. 確定要使用的**已知 Moniker**或自訂圖像名稱。

6. 在**應用修改**方法中,在返回新樹之前,在方法的某處執行以下操作,類似於下面的示例:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. 如果要創建新樹,則可以通過將所需的名字物件傳遞到 NewTree 方法來設置自定義圖像,類似於下面的範例:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>如何從真實圖像條轉換為基於名字的圖像條?
 **我需要支援HIMAGELISTs**

 如果代碼已有圖像條要更新以使用映射服務,但受需要傳遞圖像清單的 API 的限制,您仍然可以獲得映像服務的好處。 要建立基於名字的圖像條,請按照以下步驟從現有名字對象創建清單。

1. 運行 **「清單來源」** 工具,將其傳遞給影像條。 這將生成條帶的清單。

   - 建議:為清單提供非預設名稱,以適應其用法。

2. 如果您只使用**已知莫尼克斯**,則執行以下操作:

   - 將\<清單>圖像部分替換\<為 圖像/>。

   - 刪除所有子圖像指示(任何具有\<圖像行程名稱>_*)。

   - 建議:重新命名 AssetsGuid 符號和圖像條形符號,以適應其用途。

   - 將每個**包含影像**的 GUID 取代為 $(影像目錄Guid),將每個\<**包含影像**的 ID 取代為 $(名字物件>),並將外部="true"屬性添加到每個**包含影像**

       - \<名字>應該被與圖像匹配的**已知莫尼克爾**替換,但替換為"已知莫尼克器"。 從名稱中刪除。

   - 將<匯入清單\"$(清單檔夾\\)<相對安裝目錄路徑\>添加到 @Microsoft.VisualStudio.ImageCatalog.imagemanifest"/>\*到\<"符號>"部分的頂部。

       - 相對路徑由清單的設置創作中定義的部署位置確定。

3. 運行**清單ToCode**工具以生成包裝,以便現有代碼具有可用於查詢圖像條的圖像服務的名字。

   - 建議:為包裝器和命名空間提供非預設名稱,以適應其用法。

4. 執行所有添加、設置創作/部署和其他代碼更改,以便使用影像服務和新檔。

   範例清單,包括內部和外部影像,以查看它應該是什麼樣子:

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

 **我不需要支援HIMAGELISTs**

1. 確定與圖像條中的圖像匹配的**已知莫尼克斯集**,或為圖像條中的圖像創建自己的名字。

2. 更新用於在圖像條中所需索引獲取圖像的任何映射,以改用名字。

3. 更新代碼以使用影像服務通過更新的映射請求名字。 (這可能意味著更新到**CrispImage**的託管代碼,或從映射服務請求 HBITMAP 或 HICON,並將其傳遞給本機代碼。

## <a name="testing-your-images"></a>測試影像
 您可以使用圖像庫檢視器工具測試圖像清單,以確保所有內容都正確創作。 您可以在[可視化工作室 2015 SDK](visual-studio-sdk.md)中找到該工具。 此工具和其他文件[可在此處](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015)找到。

## <a name="additional-resources"></a>其他資源

### <a name="samples"></a>範例
 GitHub 上的多個 Visual Studio 範例已更新,以展示如何將影像服務用作各種 Visual Studio 擴充點的一部分。

 檢查[http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples)最新樣品。

### <a name="tooling"></a>Tooling
 為映射服務創建了一組支援工具,以幫助創建/更新與影像服務配合工作的 UI。 有關每個工具的詳細資訊,請查看工具隨附的文檔。 這些工具包含在[Visual Studio 2015 SDK](visual-studio-sdk.md)中。

 **清單來自資源**

 "來自資源清單"工具獲取圖像資源清單(PNG 或 XAML),並生成用於將這些圖像與影像服務一起使用的圖像清單檔。

 **清單代碼**

 "清單到代碼"工具採用圖像清單檔並生成一個包裝檔,用於引用代碼(C++、C#或 VB)或 *.vsct*檔中的清單值。

 **影像庫檢視器**

 圖像庫檢視器工具可以載入影像清單,並允許使用者以 Visual Studio 相同的方式操作它們,以確保該清單的創作正確。 用戶可以更改背景、大小、DPI 設置、高對比度和其他設置。 它還顯示載入資訊以查找清單中的錯誤,並顯示清單中每個圖像的源資訊。

## <a name="faq"></a>常見問題集

- 載入\<參考包含時必須包含的任何依賴項。"Microsoft.VisualStudio.*"。Interop.14.0.設計時間"/>?

  - 在所有互通 DLL 上設置嵌入 InteropType="true"

- 如何使用擴展部署映射清單?

  - 將 *.image 清單*檔添加到專案中。

  - 將「包含在 VSIX 中」設定為「true」。

- 我正在更新我的 CPS 專案系統。 **圖片名稱**和**庫存服務**發生了什麼?

  - 當 CPS 更新以使用名字器時,這些刪除。 您不再需要調用**StockIcon 服務**,只需使用 CPS 實用程式中的**ToProjectSystemType()** 擴充方法將所需的**已知 Moniker**傳遞給方法或屬性即可。 您可以在下面找到從**影像名稱**到**已知莫尼克斯的**映射:

    |||
    |-|-|
    |**ImageName**|**已知莫尼克爾**|
    |圖片名稱.離線網路應用|已知影像 Ids.Web|
    |影像名稱.Web引用資料夾|已知影像 Ids.Web|
    |影像名稱.開啟參考資料夾|已知影像 Id.資料夾開啟|
    |影像名稱.參考資料夾|已知影像 Id.參考|
    |影像名稱.參考|已知影像 Id.參考|
    |影像名稱.SdlWeb參考|已知影像 Id.Web 參考資料夾|
    |圖片名稱.DiscoWeb參考|已知影像 Id.動態探索文件|
    |影像名稱.資料夾|已知影像 Id.資料夾已關閉|
    |影像名稱.開啟資料夾|已知影像 Id.資料夾開啟|
    |影像名稱.排除資料夾|已知影像 Id.隱藏資料夾已關閉|
    |影像名稱.開啟排除資料夾|已知影像 Id.隱藏資料夾開啟|
    |影像名稱.排除檔案|已知影像 Id.隱藏檔案|
    |影像名稱.從屬檔案|已知影像 Id.產生檔案|
    |影像名稱.缺少檔案|已知影像 Id.文件警告|
    |影像名稱.視窗表單|已知影像 Id.WindowsForm|
    |影像名稱.Windows使用者控制|已知影像 Id.使用者控制|
    |影像名稱.視窗元件|已知影像 Id.元件檔案|
    |影像名稱.XmlSchema|已知影像 Ids.XMLSchema|
    |影像名稱.Xml檔案|已知影像 Ids.XML 檔案|
    |圖片名稱.WebForm|已知影像 Ids.Web|
    |圖片名稱.Web服務|已知影像 Ids.Web 服務|
    |影像名稱.Web使用者控制|已知影像 Id.Web 使用者控制|
    |影像名稱.Web自訂使用者控制|已知影像 Id.Web 自訂控制|
    |圖片名稱.Asppage|已知影像 Id.ASP 檔案|
    |影像名稱.全域應用程式類別|已知影像 Id.設定檔|
    |圖片名稱.Web 設定|已知影像 Id.設定檔|
    |圖片名稱.htmlPage|已知影像 Ids.HTML 檔案|
    |影像名稱.樣式表|已知影像 Id.樣式表|
    |影像名稱.文稿檔案|已知影像 Id.JSScript|
    |圖片名稱.文字檔|已知影像 Id.文件|
    |影像名稱.設定檔|已知影像 Id.設定|
    |影像名稱.資源|已知影像 Id.文件群組|
    |影像名稱.點陣圖|已知影像 Id.影像|
    |影像名稱.圖示|已知影像 Id.圖示檔案|
    |影像名稱.影像|已知影像 Id.影像|
    |影像名稱.影像映射|已知影像 Id.影像映射檔|
    |圖片名稱.X世界|已知影像 Ids.XWorldFile|
    |影像名稱.音訊|已知影像 Ids.聲音|
    |圖片名稱.視訊|已知影像 Id.媒體|
    |影像名稱.Cab|已知影像 Id.CAB 專案|
    |影像名稱.Jar|已知影像 Ids.JARFile|
    |影像名稱.資料環境|已知影像 Id.資料表|
    |影像名稱.預覽檔案|已知影像 Ids.報告|
    |影像名稱.懸空參考|已知影像 Id.參考警告|
    |影像名稱.Xslt 檔案|已知影像 Id.XSL 轉換|
    |影像名稱.游標|已知影像 Id.游標檔案|
    |影像名稱.應用程式設計資料夾|已知影像 Id.屬性|
    |影像名稱.資料|已知影像 Id 資料庫|
    |影像名稱.應用程式|已知影像 Id.應用程式|
    |影像名稱.資料集|已知影像 Id 資料庫群組|
    |影像名稱.Pfx|已知影像 Id.憑證|
    |影像名稱.Snk|已知影像 Id.Rule|
    |影像名稱.視覺化基礎專案|已知影像 Id.VB 專案節點|
    |影像名稱.C夏普專案|已知影像 Id.CSProjectNode|
    |影像名稱.空|已知影像 Id.Blank|
    |影像名稱.缺少資料夾|已知影像 Id.資料夾離線|
    |影像名稱.共用匯入參考|已知影像 Id.共用專案|
    |影像名稱.共用專案|已知影像 Ids.CS 共享專案|
    |影像名稱.共用專案Vc|已知影像 Id.CPP 分享專案|
    |影像名稱.共用專案J|已知影像 Ids.JS 分享專案|
    |影像名稱.C夏普代碼檔案|已知影像 Id.CSFileNode|
    |影像名稱.視覺基本代碼檔案|已知影像 Id.VBFileNode|

  - 我正在更新我的完成清單提供程式。 什麼**已知莫尼克器**與舊的**標準字形組**和**標準字**形值相匹配?

    ||||
    |-|-|-|
    |字形組類別|字形項目公開|類公共|
    |字形組類別|字形項目內部|類別|
    |字形組類別|字形專案朋友|類別|
    |字形組類別|字形項目保護|類保護|
    |字形組類別|字型專案私人|類私有|
    |字形組類別|字型專案快捷方式|類別快捷方式|
    |字形群組常數|字形項目公開|常量公共|
    |字形群組常數|字形項目內部|常量內部|
    |字形群組常數|字形專案朋友|常量內部|
    |字形群組常數|字形項目保護|恒定保護|
    |字形群組常數|字型專案私人|常點私人|
    |字形群組常數|字型專案快捷方式|常巧快捷|
    |字形組代表|字形項目公開|委託公共|
    |字形組代表|字形項目內部|委託內部|
    |字形組代表|字形專案朋友|委託內部|
    |字形組代表|字形項目保護|委託保護|
    |字形組代表|字型專案私人|委託私人|
    |字形組代表|字型專案快捷方式|委託快捷方式|
    |字形群組|字形項目公開|枚舉公共|
    |字形群組|字形項目內部|列舉內部|
    |字形群組|字形專案朋友|列舉內部|
    |字形群組|字形項目保護|枚舉保護|
    |字形群組|字型專案私人|枚舉私人|
    |字形群組|字型專案快捷方式|列舉快捷方式|
    |字形群組成員|字形項目公開|列舉項目公開|
    |字形群組成員|字形項目內部|列舉項目內部|
    |字形群組成員|字形專案朋友|列舉項目內部|
    |字形群組成員|字形項目保護|列舉項目保護|
    |字形群組成員|字型專案私人|Enum 專案專用|
    |字形群組成員|字型專案快捷方式|列舉專案快捷方式|
    |字型集團事件|字形項目公開|事件公共|
    |字型集團事件|字形項目內部|事件內部|
    |字型集團事件|字形專案朋友|事件內部|
    |字型集團事件|字形項目保護|事件保護|
    |字型集團事件|字型專案私人|事件私人|
    |字型集團事件|字型專案快捷方式|事件快捷方式|
    |字形群組例外|字形項目公開|異常公共|
    |字形群組例外|字形項目內部|異常內部|
    |字形群組例外|字形專案朋友|異常內部|
    |字形群組例外|字形項目保護|異常保護|
    |字形群組例外|字型專案私人|例外私有|
    |字形群組例外|字型專案快捷方式|例外捷徑|
    |字形群組場|字形項目公開|現場公共|
    |字形群組場|字形項目內部|欄位內部|
    |字形群組場|字形專案朋友|欄位內部|
    |字形群組場|字形項目保護|現場保護|
    |字形群組場|字型專案私人|欄位私人|
    |字形群組場|字型專案快捷方式|欄位快捷方法|
    |字形群組介面|字形項目公開|介面公共|
    |字形群組介面|字形項目內部|介面內部|
    |字形群組介面|字形專案朋友|介面內部|
    |字形群組介面|字形項目保護|介面保護|
    |字形群組介面|字型專案私人|介面專用|
    |字形群組介面|字型專案快捷方式|介面快捷方式|
    |字形集團Macro|字形項目公開|宏公共|
    |字形集團Macro|字形項目內部|宏內部|
    |字形集團Macro|字形專案朋友|宏內部|
    |字形集團Macro|字形項目保護|宏保護|
    |字形集團Macro|字型專案私人|宏私有|
    |字形集團Macro|字型專案快捷方式|巨集快捷方式|
    |字形組圖|字形項目公開|地圖公共|
    |字形組圖|字形項目內部|地圖內部|
    |字形組圖|字形專案朋友|地圖內部|
    |字形組圖|字形項目保護|地圖保護|
    |字形組圖|字型專案私人|地圖專用|
    |字形組圖|字型專案快捷方式|地圖快捷方式|
    |字形群組對應項目|字形項目公開|地圖專案公共|
    |字形群組對應項目|字形項目內部|映射項目內部|
    |字形群組對應項目|字形專案朋友|映射項目內部|
    |字形群組對應項目|字形項目保護|地圖項目保護|
    |字形群組對應項目|字型專案私人|映射項目私有|
    |字形群組對應項目|字型專案快捷方式|對應專案快捷|
    |字型群組方法|字形項目公開|方法公開|
    |字型群組方法|字形項目內部|方法內部|
    |字型群組方法|字形專案朋友|方法內部|
    |字型群組方法|字形項目保護|MethodProtected|
    |字型群組方法|字型專案私人|方法私有|
    |字型群組方法|字型專案快捷方式|方法快捷方式|
    |字形群組載入|字形項目公開|方法公開|
    |字形群組載入|字形項目內部|方法內部|
    |字形群組載入|字形專案朋友|方法內部|
    |字形群組載入|字形項目保護|MethodProtected|
    |字形群組載入|字型專案私人|方法私有|
    |字形群組載入|字型專案快捷方式|方法快捷方式|
    |字形群組模組|字形項目公開|模組公共|
    |字形群組模組|字形項目內部|模組內部|
    |字形群組模組|字形專案朋友|模組內部|
    |字形群組模組|字形項目保護|模組保護|
    |字形群組模組|字型專案私人|模組私有|
    |字形群組模組|字型專案快捷方式|模組快捷方式|
    |字形命名空間|字形項目公開|命名空間公共|
    |字形命名空間|字形項目內部|命名空間內部|
    |字形命名空間|字形專案朋友|命名空間內部|
    |字形命名空間|字形項目保護|命名空間保護|
    |字形命名空間|字型專案私人|命名空間私人|
    |字形命名空間|字型專案快捷方式|命名空間快捷方式|
    |字形組管理員|字形項目公開|操作員公共|
    |字形組管理員|字形項目內部|操作員內部|
    |字形組管理員|字形專案朋友|操作員內部|
    |字形組管理員|字形項目保護|操作員保護|
    |字形組管理員|字型專案私人|操作員私人|
    |字形組管理員|字型專案快捷方式|操作員快捷方式|
    |字形集團屬性|字形項目公開|屬性公開|
    |字形集團屬性|字形項目內部|屬性內部|
    |字形集團屬性|字形專案朋友|屬性內部|
    |字形集團屬性|字形項目保護|屬性保護|
    |字形集團屬性|字型專案私人|屬性私人|
    |字形集團屬性|字型專案快捷方式|屬性快捷方式|
    |字形組結構|字形項目公開|結構公共|
    |字形組結構|字形項目內部|結構內部|
    |字形組結構|字形專案朋友|結構內部|
    |字形組結構|字形項目保護|結構保護|
    |字形組結構|字型專案私人|結構私有|
    |字形組結構|字型專案快捷方式|結構快捷方式|
    |字形組樣本|字形項目公開|樣本公開|
    |字形組樣本|字形項目內部|樣本內部|
    |字形組樣本|字形專案朋友|樣本內部|
    |字形組樣本|字形項目保護|樣本保護|
    |字形組樣本|字型專案私人|樣本專用|
    |字形組樣本|字型專案快捷方式|樣本快捷方法|
    |字型群組類型def|字形項目公開|類型定義公共|
    |字型群組類型def|字形項目內部|型態定義內部|
    |字型群組類型def|字形專案朋友|型態定義內部|
    |字型群組類型def|字形項目保護|型態定義保護|
    |字型群組類型def|字型專案私人|型態定義私有|
    |字型群組類型def|字型專案快捷方式|型態定義快捷方式|
    |字形群組型|字形項目公開|類型公共|
    |字形群組型|字形項目內部|型態內部|
    |字形群組型|字形專案朋友|型態內部|
    |字形群組型|字形項目保護|型別保護|
    |字形群組型|字型專案私人|型態私人|
    |字形群組型|字型專案快捷方式|型態快捷方式|
    |字形群組聯盟|字形項目公開|聯合公共|
    |字形群組聯盟|字形項目內部|聯合內部|
    |字形群組聯盟|字形專案朋友|聯合內部|
    |字形群組聯盟|字形項目保護|聯盟保護|
    |字形群組聯盟|字型專案私人|聯合私人|
    |字形群組聯盟|字型專案快捷方式|以快速的快捷方式|
    |字形組變數|字形項目公開|現場公共|
    |字形組變數|字形項目內部|欄位內部|
    |字形組變數|字形專案朋友|欄位內部|
    |字形組變數|字形項目保護|現場保護|
    |字形組變數|字型專案私人|欄位私人|
    |字形組變數|字型專案快捷方式|欄位快捷方法|
    |字型組值類型|字形項目公開|價值類型公共|
    |字型組值類型|字形項目內部|值類型 內部|
    |字型組值類型|字形專案朋友|值類型 內部|
    |字型組值類型|字形項目保護|價值類型保護|
    |字型組值類型|字型專案私人|值類型私有|
    |字型組值類型|字型專案快捷方式|值型別快捷|
    |字形群組內生|字形項目公開|物件公共|
    |字形群組內生|字形項目內部|物件內部|
    |字形群組內生|字形專案朋友|物件內部|
    |字形群組內生|字形項目保護|物件保護|
    |字形群組內生|字型專案私人|物件專用|
    |字形群組內生|字型專案快捷方式|物件快捷方式|
    |字形群組J夏普法|字形項目公開|方法公開|
    |字形群組J夏普法|字形項目內部|方法內部|
    |字形群組J夏普法|字形專案朋友|方法內部|
    |字形群組J夏普法|字形項目保護|MethodProtected|
    |字形群組J夏普法|字型專案私人|方法私有|
    |字形群組J夏普法|字型專案快捷方式|方法快捷方式|
    |字形組J夏普菲爾德|字形項目公開|現場公共|
    |字形組J夏普菲爾德|字形項目內部|欄位內部|
    |字形組J夏普菲爾德|字形專案朋友|欄位內部|
    |字形組J夏普菲爾德|字形項目保護|現場保護|
    |字形組J夏普菲爾德|字型專案私人|欄位私人|
    |字形組J夏普菲爾德|字型專案快捷方式|欄位快捷方法|
    |字形群組J夏普類|字形項目公開|類公共|
    |字形群組J夏普類|字形項目內部|類別|
    |字形群組J夏普類|字形專案朋友|類別|
    |字形群組J夏普類|字形項目保護|類保護|
    |字形群組J夏普類|字型專案私人|類私有|
    |字形群組J夏普類|字型專案快捷方式|類別快捷方式|
    |字形群組J夏普命名空間|字形項目公開|命名空間公共|
    |字形群組J夏普命名空間|字形項目內部|命名空間內部|
    |字形群組J夏普命名空間|字形專案朋友|命名空間內部|
    |字形群組J夏普命名空間|字形項目保護|命名空間保護|
    |字形群組J夏普命名空間|字型專案私人|命名空間私人|
    |字形群組J夏普命名空間|字型專案快捷方式|命名空間快捷方式|
    |字形組JJJJ介面|字形項目公開|介面公共|
    |字形組JJJJ介面|字形項目內部|介面內部|
    |字形組JJJJ介面|字形專案朋友|介面內部|
    |字形組JJJJ介面|字形項目保護|介面保護|
    |字形組JJJJ介面|字型專案私人|介面專用|
    |字形組JJJJ介面|字型專案快捷方式|介面快捷方式|
    |字形群組錯誤||StatusError|
    |字形BscFile||類別檔案|
    |字形組裝||參考|
    |字型庫||程式庫|
    |字形VB專案||VB專案節點|
    |字形酷項目||CS 專案節點|
    |字型方案專案||CPP 專案節點|
    |字型對話Id||對話|
    |字型開啟資料夾||資料夾已開啟|
    |字形封閉資料夾||資料夾已關閉|
    |字形箭||到下一個|
    |字形C夏普檔案||CSFileNode|
    |字形C夏普擴展||程式碼片段|
    |字形關鍵字||感知關鍵字|
    |字型資訊||狀態資訊|
    |字形參考||類別參考|
    |字形再體||遞迴|
    |字形專案||Tag|
    |字形JJ夏普專案||DocumentCollection|
    |字形J夏普檔案||Document|
    |字型前進類型||到下一個|
    |字型呼叫圖||通話|
    |字型標記||從|
    |字形警告||StatusWarning|
    |字形參考||問題標記|
    |字型可能呼叫者||通話|
    |字型可能呼叫||從|
    |字形延伸法||擴充方法|
    |字型延伸方法內部||擴充方法|
    |字形延伸方法朋友||擴充方法|
    |字型延伸方法保護||擴充方法|
    |字型延伸方法私人||擴充方法|
    |字型延伸方法快捷方式||擴充方法|
    |字形Xml屬性||XmlAttribute|
    |字形兒童||XmlElement|
    |字形||XmlDescendant|
    |字形命名空間||XmlNamespace|
    |字形屬性問題||XmlAttribute 低信心|
    |字形屬性檢查||XmlAttribute 高度自信|
    |字形兒童問題||XmlElement 低信心|
    |字形兒童檢查||XmlElement 高度自信|
    |字形下降問題||XmlSsLowss 低信心|
    |字形降驗||XmlDescendant高信心|
    |字形完成警告||感知警告|
