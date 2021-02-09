---
title: 解決 DPI Issues2 |Microsoft Docs
description: 瞭解針對高解析度畫面進行程式設計時所牽涉到的問題，例如相應增加內容、配置問題，以及使用 DPI 調整 Api。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8151748b946d2c1b5ad21359569d6f5f856f9250
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876156"
---
# <a name="address-dpi-issues"></a>解決 DPI 問題
以「高解析度」畫面出貨的裝置數量會增加。 這些畫面的每英寸通常有超過200圖元 (ppi) 。 在這些電腦上使用應用程式需要相應增加內容，以符合在裝置上以一般觀賞距離來查看內容的需求。 從2014，高密度顯示器的主要目標是行動裝置電腦 (平板電腦、clamshell 膝上型電腦和手機) 。

Windows 8.1 和更高版本包含數個功能，可讓這些機器使用電腦同時連結至高密度和標準密度的顯示器和環境。

- Windows 可讓您使用 Windows XP) 之後的「讓文字和其他專案變得更大或更小」 (設定，將內容調整至裝置。

- Windows 8.1 和更新版本會自動調整內容，讓大部分的應用程式在顯示不同的圖元密度之間移動時保持一致。 當主要顯示器為高密度 (200% 的縮放比例) ，而次要顯示器是標準密度 (100% ) 時，Windows 會自動將次要顯示器上的應用程式視窗內容縮小， (應用程式) 轉譯的每4個圖元顯示1個圖元。

- Windows 將預設為圖元密度的正確調整，以及顯示 (Windows 7 和更新版本、OEM 可設定) 的觀看距離。

- 從 Windows 8.1 S14) ，Windows 可以在超過 280 ppi (的新裝置上，自動將內容調整為250%。

  Windows 有一種方法可以處理相應放大的 UI，以利用增加的圖元數。 應用程式會藉由宣告本身的「系統 DPI 感知」來加入宣告此系統。 不這麼做的應用程式會由系統相應增加。 這可能會導致「模糊」使用者體驗，其中整個應用程式都一致地調整圖元。 例如：

  ![DPI 模糊問題](../extensibility/media/dpi-issues-fuzzy.png "DPI 模糊問題")

  Visual Studio 選擇採用 DPI 調整感知，因此不會「虛擬化」。

  Windows (和 Visual Studio) 運用數種 UI 技術，這些技術具有不同的方式來處理系統所設定的調整因素。 例如：

- WPF 會以與裝置無關的方式來測量控制項， (單位，而不是圖元) 。 WPF UI 會自動擴大目前的 DPI。

- 無論 UI 架構為何，所有文字大小都會以點表示，而系統會將其視為與 DPI 無關。 當您繪製到顯示裝置時，Win32、WinForms 和 WPF 中的文字已正確擴大。

- Win32/WinForms 對話方塊和視窗可讓您啟用以文字調整的版面配置 (例如，透過方格、flow 和資料表版面配置面板) 。 這些可讓您避免在字型大小增加時，不會調整的硬式編碼圖元位置。

- 系統所提供的圖示或以系統計量為基礎的資源 (例如，SM_CXICON 和 SM_CXSMICON) 已相應增加。

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>舊版 Win32 (GDI、GDI +) 和以 WinForms 為基礎的 UI
雖然 WPF 已經有高 DPI 感知，但大部分 Win32/GDI 型程式碼原本都不是以 DPI 感知來撰寫。 Windows 已提供 DPI 調整 Api。 Win32 問題的修正應該一致地在產品中使用這些問題。 Visual Studio 已提供 helper 類別庫，以避免複製功能並確保產品的一致性。

## <a name="high-resolution-images"></a>高解析度影像
本節主要適用于擴充 Visual Studio 2013 的開發人員。 針對 Visual Studio 2015，請使用 Visual Studio 內建的映射服務。 您也可能會發現您需要支援/鎖定許多版本的 Visual Studio，因此使用2015中的映射服務並不是一個選項，因為它不存在於舊版中。 這一節也適用于您。

## <a name="scaling-up-images-that-are-too-small"></a>擴充太小的影像
太小的影像可以使用一些常見的方法，在 GDI 和 WPF 上向上擴充和轉譯。 受控 DPI 協助程式類別可供內部和外部 Visual Studio 整合者用來處理縮放圖示、點陣圖、imagestrips 和 imagelists。 以 Win32 為基礎的原生 C/C + + helper 可用於調整 HICON、HBITMAP、HIMAGELIST 和 VsUI：： GdiplusImage。 點陣圖的縮放通常只需要在包含 helper 程式庫的參考之後，才需要單行變更。 例如：

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

調整 imagelist 取決於 imagelist 在載入時間是否已完成，或在執行時間附加。 如果在載入時完成，請使用 imagelist 來呼叫，就 `LogicalToDeviceUnits()` 像使用點陣圖一樣。 當程式碼在撰寫 imagelist 之前需要載入個別點陣圖時，請務必調整 imagelist 的影像大小：

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

在機器碼中，您可以在建立 imagelist 時調整維度，如下所示：

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

程式庫中的函式允許指定調整大小演算法。 調整要放置在 imagelists 中的影像時，請務必指定用於透明的背景色彩，或使用 NearestNeighbor 縮放 (，這會導致125% 和 150% ) 的扭曲。

請參閱 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN 上的檔。

下表顯示如何在相對應的 DPI 縮放比例比例調整影像的範例。 橙色所述的影像代表我們從 Visual Studio 2013 (100%-200% DPI 縮放比例) 的最佳作法：

![DPI 縮放問題](../extensibility/media/dpi-issues-scaling.png "DPI 縮放問題")

## <a name="layout-issues"></a>版面配置問題
常見的版面配置問題可避免，主要是讓 UI 中的點彼此調整，而不是使用絕對位置（ (特別是圖元單位) ）。 例如：

- 版面配置/文字位置需要調整以考慮相應放大影像。

- 格線中的資料行必須針對相應放大文字調整寬度。

- 硬式編碼大小或元素之間的空格也需要相應增加。 以文字維度為基礎的大小通常是正常的，因為字型會自動向上擴充。

  Helper 函數可在類別中使用 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> ，以允許在 X 和 Y 軸上進行縮放：

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (函式允許在 X/Y 軸上進行縮放) 

- int space = DpiHelper. LogicalToDeviceUnitsX (10) ;

- int height = VsUI：:D piHelper：： LogicalToDeviceUnitsY (5) ;

  有 LogicalToDeviceUnits 多載可讓您調整物件，例如矩形、點和大小。

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>使用 DPIHelper 程式庫/類別來調整影像和版面配置
Visual Studio DPI 協助程式程式庫適用于原生和 managed 表單，可供其他應用程式在 Visual Studio shell 之外使用。

若要使用程式庫，請移至 [VISUAL STUDIO VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 擴充性範例，並複製 High-DPI_Images_Icons 範例。

在原始程式檔中，包含 *VsUIDpiHelper* ，並呼叫類別的靜態函式 `VsUI::DpiHelper` ：

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> 請勿在模組層級或類別層級靜態變數中使用 helper 函數。 此程式庫也會使用靜態來進行執行緒同步處理，而您可能會遇到順序初始化問題。 將這些靜態變數轉換成非靜態成員變數，或將它們包裝到函式 (，以便在第一次存取) 上進行結構化。

從將在 Visual Studio 環境內執行的 managed 程式碼存取 DPI 協助程式函式：

- 取用專案必須參考最新版本的 Shell MPF。 例如：

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- 確定專案具有 **PresentationCore** 和 **PresentationUI** 的 **參考。**

- 在程式碼中，請使用 **VisualStudio PlatformUI** 命名空間，並呼叫 DpiHelper 類別的靜態函式。 針對支援的型別 (點、大小、矩形等等) ，提供的擴充功能會傳回新的縮放物件。 例如：

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>在可 UI 中處理 WPF 影像的顏色
在 WPF 中，WPF 會使用高品質的雙立方演算法 (預設) （適用于圖片或大型螢幕擷取畫面）為目前的 DPI 縮放層級自動調整大小，但不適合功能表項目圖示，因為它引進了察覺的調整大小。

建議：

- 針對標誌影像和橫幅圖稿，可以使用預設的重設 <xref:System.Windows.Media.BitmapScalingMode> 大小模式。

- 針對功能表項目和圖示影像， <xref:System.Windows.Media.BitmapScalingMode> 當它不會造成其他扭曲成品消除重設 (（200% 和 300% ) ）時，應該使用。

- 針對大型縮放層級，不是 100% (的倍數（例如250% 或 350% ) ），以雙全半形調整圖示影像會產生模糊、沖蝕的 UI。 首先，將具有 NearestNeighbor 的影像調整為 100% (的最大倍數（例如200% 或 300% ) ，並從該處調整雙立方，以獲得更好的結果。 請參閱特殊案例：如需詳細資訊，請 prescaling 適用于大型 DPI 層級的 WPF 影像。

  VisualStudio. PlatformUI 命名空間中的 DpiHelper 類別提供可用於系結的成員 <xref:System.Windows.Media.BitmapScalingMode> 。 這可讓 Visual Studio shell 一致地控制整個產品的點陣圖縮放模式，視 DPI 縮放比例而定。

  若要在 XAML 中使用它，請新增：

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio shell 已在最上層視窗和對話方塊上設定此屬性。 以 WPF 為基礎的 UI 在 Visual Studio 中執行時，已將它繼承。 如果設定未傳播至您的特定 UI 片段，可以在 XAML/WPF UI 的根項目上設定。 發生這種情況的地方包括快顯視窗、具有 Win32 父代的專案，以及用完進程的設計工具視窗，例如 Blend。

某些 UI 可與系統設定的 DPI 縮放層級分開調整，例如 Visual Studio 文字編輯器和 WPF 型設計工具 (WPF Desktop 和 Windows Store) 。 在這些情況下，不應該使用 DpiHelper System.windows.media.bitmapscalingmode>。 為了修正編輯器中的這個問題，IDE 小組建立了一個名為 System.windows.media.renderoptions>. System.windows.media.bitmapscalingmode> 的自訂屬性。 根據系統和 UI 的合併縮放層級，將該屬性值設定為 HighQuality 或 NearestNeighbor。

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊案例： prescaling 適用于大型 DPI 層級的 WPF 影像
針對不是 100% (倍數的極大縮放層級（例如250%、350% 等）) ，以雙立方調整圖示影像會產生模糊、沖蝕的 UI。 這些影像與清晰文字的印象幾乎就像光學假像一樣。 影像看起來會比文字更接近眼睛和焦點。 您可以先將 NearestNeighbor 的影像調整為 100% (的最大倍數（例如200% 或 300% ) ，並 (以雙立方重設為額外的 50% ) ，來改善此放大規模的調整結果。

以下是結果中差異的範例，其中第一個影像會以改良的雙調整演算法 100%->200%->250%，而第二個則是使用雙立方 100% >250%。

![DPI 問題雙重調整範例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 問題雙重調整範例")

為了讓 UI 能夠使用這個雙重調整，必須修改用於顯示每個影像元素的 XAML 標記。 下列範例示範如何使用 DpiHelper 程式庫和 Shell. 12/14，在 Visual Studio 中使用 WPF 的雙重調整。

步驟1：使用 NearestNeighbor 將映射 Prescale 至200%、300% 等等。

使用在系結上套用的轉換器或使用 XAML 標記延伸來 Prescale 影像。 例如：

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

如果映射也需要主題 (大部分（但不是全部）都應該) ，標記可以使用不同的轉換器，以先進行映射的主題然後預先調整。 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> 根據所需的轉換輸出，標記可以使用或。

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

步驟2：確定最終大小對於目前的 DPI 而言是正確的。

由於 WPF 會使用在 UIElement 上設定的 System.windows.media.bitmapscalingmode> 屬性來調整目前 DPI 的 UI，因此使用 prescaled 影像做為其來源的影像控制項，將會看到比它更大的兩或三倍。 以下有幾種方式可對付此效果：

- 如果您知道原始影像在100% 的維度，則可以指定影像控制項的確切大小。 這些大小會反映 UI 的大小，然後才套用調整。

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- 如果原始影像的大小不是已知的，則可以使用 LayoutTransform 來縮小最終的影像物件。 例如：

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>啟用 WebOC 的 HDPI 支援
根據預設，WebOC 會控制 (（例如 WPF 中的 WebBrowser 控制項）或 IWebBrowser2 介面，) 不啟用 HDPI 偵測和支援。 結果會是內嵌控制項，其顯示的內容在高解析度顯示時太小。 以下說明如何啟用特定 web WebOC 實例中的高 DPI 支援。

執行 IDocHostUIHandler 介面 (請參閱 [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))的 MSDN 文章：

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

（選擇性）執行 ICustomDoc 介面 (請參閱 [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))的 MSDN 文章：

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

將執行 IDocHostUIHandler 的類別與 WebOC 的檔產生關聯。 如果您已執行上述的 ICustomDoc 介面，則只要 WebOC 的 document 屬性有效，就會將它轉換成 ICustomDoc 並呼叫 SetUIHandler 方法，並傳遞可執行 IDocHostUIHandler 的類別。

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

如果您未執行 ICustomDoc 介面，則只要 WebOC 的 document 屬性都有效，您就必須將它轉換成 IOleObject，然後呼叫 `SetClientSite` 方法，傳入可執行 IDocHostUIHandler 的類別。 在傳遞至方法呼叫的 DOCHOSTUIINFO 上設定 DOCHOSTUIFLAG_DPI_AWARE 旗標 `GetHostInfo` ：

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

這應該是您取得 WebOC 控制項以支援 HPDI 所需的一切。

## <a name="tips"></a>提示

1. 如果 WebOC 控制項上的 document 屬性變更，您可能需要將檔與 IDocHostUIHandler 類別重新關聯。

2. 如果上述動作無法運作，WebOC 就會有一個已知問題，就是無法挑選 DPI 旗標的變更。 最可靠的修正方法是切換 WebOC 的光學縮放，這表示兩個不同值的兩個呼叫會顯示比例百分比。 此外，如果需要此因應措施，則可能需要在每個流覽呼叫上執行此因應措施。

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
