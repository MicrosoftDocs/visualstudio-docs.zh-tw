---
title: 解決 DPI 問題2 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740101"
---
# <a name="address-dpi-issues"></a>解決 DPI 問題
越來越多的設備使用"高解析度"屏幕發貨。 這些螢幕通常每英寸 (ppi) 超過 200 圖元。 使用這些電腦上的應用程式需要放大內容,以滿足在設備正常查看距離下查看內容的需求。 截至 2014 年,高密度顯示器的主要目標是行動計算裝置(平板電腦、翻蓋筆記型電腦和手機)。

Windows 8.1 及更高版本包含多個功能,使這些計算機能夠同時處理顯示器和計算機同時連接到高密度和標準密度顯示器的環境。

- Windows 允許您使用"使文本和其他項目變大或更小"設置(自 Windows XP 以來可用)將內容縮放到設備。

- Windows 8.1 和更高版本將自動縮放大多數應用程式的內容,在圖元密度不同的顯示之間移動時,內容將保持一致。 當主顯示器為高密度(200% 縮放),而輔助顯示器為標準密度(100%),Windows 將自動在輔助顯示器上向下縮放應用程式視窗內容(應用程式渲染的每 4 個像素顯示 1 個畫素)。

- Windows 將預設為顯示的圖元密度和查看距離(Windows 7 及更高版本,OEM 可配置)的右縮放。

- Windows 可以在超過 280 ppi 的新設備上自動縮放內容高達 250%(截至 Windows 8.1 S14)。

  Windows 有一種處理向上擴展 UI 的方法,以利用增加的圖元計數。 應用程式通過聲明自身為"系統 DPI 感知"來加入加入此系統。 不這樣做的應用程式將由系統放大。 這可能導致"模糊"用戶體驗,其中整個應用程式均勻地拉伸圖元。 例如：

  ![DPI 模糊問題](../extensibility/media/dpi-issues-fuzzy.png "DPI 模糊問題")

  Visual Studio 選擇成為 DPI 縮放感知,因此不是「虛擬化」。。

  Windows(和 Visual Studio)利用多種 UI 技術,這些技術在處理系統設置的縮放因素時有不同的處理方式。 例如：

- WPF 以獨立於設備的方式測量控件(單位,而不是圖元)。 WPF UI 會自動擴展當前 DPI。

- 所有文本大小,無論 UI 框架如何,都以點表示,因此系統將文本大小視為獨立於 DPI 的。 Win32、WinForms 和 WPF 中的文本在繪製到顯示設備時已正確放大。

- Win32/WinForms 對話框和視窗具有啟用使用文本調整大小的佈局(例如,通過網格、流和錶佈局面板)的佈局的方法。 這些功能可避免在字體大小增加時未縮放的硬編碼圖元位置。

- 系統或資源基於系統指標(例如,SM_CXICON和SM_CXSMICON)提供的圖示已放大。

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>較舊的 Win32(GDI、GDI+)和基於 WinForms 的 UI
雖然 WPF 已經對 DPI 感知很高,但我們大部分基於 Win32/GDI 的代碼最初並不是在考慮到 DPI 意識的情況下編寫的。 Windows 提供了 DPI 縮放 API。 Win32 問題的修復應在整個產品中一致地使用這些問題。 Visual Studio 提供了一個幫助器類庫,以避免複製功能並確保整個產品的一致性。

## <a name="high-resolution-images"></a>高解析度影像
本節主要面向擴展 Visual Studio 2013 的開發人員。 對於 Visual Studio 2015,請使用內建於視覺工作室的圖像服務。 您可能還會發現,您需要支援/定位 Visual Studio 的許多版本,因此在 2015 年使用影像服務不是一個選項,因為它在以前的版本中並不存在。 本部分也適合您。

## <a name="scaling-up-images-that-are-too-small"></a>放大太小的影像
使用一些常用方法,可以在 GDI 和 WPF 上放大和渲染太小的圖像。 託管 DPI 協助器類別可供內部和外部 Visual Studio 整合商使用,用於解決縮放圖示、點陣圖、圖像繪製和影像清單。 基於 Win32 的本機 C/C++幫助器可用於縮放 HICON、HBITMAP、HIMAGELIST 和 VsUI:GdiplusImage。 位圖的縮放通常只需要在包含對幫助器庫的引用後進行單行更改。 例如：

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

縮放影像清單取決於映射清單是在載入時完成,還是在運行時追加。 如果在載入時完成,請像`LogicalToDeviceUnits()`使用位圖一樣調用圖像清單。 當代碼在撰寫影像清單之前需要載入單個點陣圖時,請確保縮放影像清單的影像大小:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

在本機代碼中,建立影像清單時可以縮放維度,如下所示:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

庫中的函數允許指定大小調整演演演算法。 縮放要放置在圖像清單中的圖像時,請確保指定用於透明度的背景顏色,或使用「最近鄰居」縮放(這將導致 125% 和 150% 的扭曲)。

請參閱<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN 上的文檔。

下表顯示了如何在相應的 DPI 縮放因數下縮放圖像的範例。 橙色中概述的圖像表示我們截至 Visual Studio 2013 的最佳實踐(100%-200% DPI 縮放):

![DPI 縮放問題](../extensibility/media/dpi-issues-scaling.png "DPI 縮放問題")

## <a name="layout-issues"></a>配置問題
常見的佈局問題主要通過在 UI 中縮放和相對於彼此而不是使用絕對位置(特別是以像素單位為單位)來避免。 例如：

- 佈局/文本位置需要調整,以考慮放大的圖像。

- 網格中的列需要調整縮放文本的寬度。

- 還需要放大元素之間的硬編碼大小或空間。 僅基於文本尺寸的大小通常正常,因為字體會自動縮小。

  <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>說明器函數在類中可用,允許在 X 軸和 Y 軸上縮放:

- 邏輯到裝置單位X/邏輯到裝置單元Y(功能允許在 X/Y 軸上縮放)

- 內空間 = DpiHelper.邏輯到設備單元X (10);

- int 高度 = VsUI::DpiHelper::邏輯到設備單元(5);

  有邏輯到設備單元重載,允許縮放物件,如 Rect、點和大小。

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>使用 DPIHelper 函式庫/類別縮放影像和佈局
Visual Studio DPI 幫助器庫以本機和託管形式提供,其他應用程式可以在 Visual Studio 外殼之外使用。

要使用庫,請造訪 Visual [Studio VSSDK 擴充性範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)並克隆高DPI_Images_Icons示例。

在來源檔案中,包括*VsUIDpiHelper.h*並呼叫`VsUI::DpiHelper`類的 靜態函數:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> 請勿在模組級或類級靜態變數中使用説明器函數。 庫還使用靜態進行線程同步,並且可能會遇到訂單初始化問題。 將這些靜態變數轉換為非靜態成員變數,或將它們包裝成一個函數(因此,它們在第一次訪問時構造)。

要從從 Visual Studio 環境執行的託管代碼存取 DPI 說明器函數,請執行以下服務:

- 使用項目必須引用最新版本的殼牌 MPF。 例如：

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- 確保專案具有對**System.Windows.窗體**、**演示文稿核心**和演示文稿**UI**的引用。

- 在代碼中,使用**Microsoft.VisualStudio.PlatformUI**命名空間,並調用 DpiHelper 類的靜態函數。 對於受支援的類型(點、大小、矩形等),提供了返回新縮放物件的擴展函數。 例如：

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>處理可縮放 UI 中的 WPF 影像模糊性
在 WPF 中,位圖由 WPF 自動調整當前 DPI 縮放級別的大小,使用高品質的雙立方演演演算法(預設),該演演演算法適用於圖片或大型螢幕截圖,但不適合功能表本圖示,因為它引入了感知的模糊性。

建議：

- 對於徽標圖像和橫幅圖稿,可以使用<xref:System.Windows.Media.BitmapScalingMode>默認調整大小模式。

- 對選單項目與圖示影像,<xref:System.Windows.Media.BitmapScalingMode>當它不會導致其他失真偽影消除模糊性(200% 和 300%)時,應使用 。

- 對於大型變焦級別,不要出現 100% 的倍數(例如,250% 或 350%),使用雙立方縮放圖標圖像會導致模糊、沖刷的 UI。 首先將離鄰將影像縮放到最大倍數 100%(例如,200% 或 300%)時,可以獲得更好的結果並從那裡用雙立方進行縮放。 有關詳細資訊,請參閱特殊情況:針對大型 DPI 級別的預縮放 WPF 映射。

  Microsoft.VisualStudio.PlatformUI 命名空間中的 DpiHelper 類<xref:System.Windows.Media.BitmapScalingMode>提供了可用於 綁定的成員。 它將允許 Visual Studio 外殼根據 DPI 縮放因數統一控制整個產品的位圖縮放模式。

  要在 XAML 中使用它,添加:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio 外殼已在頂級視窗和對話框上設置此屬性。 在可視化工作室中運行的基於 WPF 的 UI 將繼承它。 如果該設置未傳播到特定 UI 部分,則可以在 XAML/WPF UI 的根元素上設置該設置。 發生這種情況的地方包括彈出視窗、具有 Win32 父元素的元素以及進程用完的設計師視窗(如 Blend)。

某些 UI 可以獨立於系統設定的 DPI 縮放等級進行縮放,例如可視化工作室文本編輯器和基於 WPF 的設計器(WPF 桌面和 Windows 應用商店)。 在這些情況下,不應使用 DpiHelper.位映射縮放模式。 為了在編輯器中解決此問題,IDE 團隊創建了一個自定義屬性,名為"呈現選項.BitmapScalingMode"。 根據系統和 UI 的組合縮放級別,將該屬性值設置為"高品質" 或「 最近鄰居」。

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊情況:針對大型 DPI 等級的預縮放 WPF 映射
對於不是 100% 的倍數(例如,250%、350% 等)的非常大的縮放級別,使用雙立方縮放圖示圖像會導致模糊、衝出 UI。 這些圖像與清晰文本的印象幾乎類似於一個光學錯覺。 圖像似乎更接近眼睛,與文本無關。 以首先將「最近鄰居」的影像縮放到最大倍數 100%(例如 200% 或 300%),可以改進此放大大小的縮放結果用雙立方縮放到其餘部分(額外 50%)。

下面是結果差異的示例,其中第一個圖像使用改進的雙縮放演演演算法 100%->200%->250%進行縮放,第二個圖像僅以雙立方 100%->250% 進行縮放。

![DPI 發出雙重縮放範例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 發出雙重縮放範例")

為了使 UI 能夠使用此雙縮放,需要修改用於顯示每個圖像元素的 XAML 標記。 以下示例演示如何在 Visual Studio 中使用 DpiHelper 庫和 Shell.12/14 在 WPF 中使用雙縮放。

步驟 1:使用「最近鄰居」將圖像預縮放為 200%、300%,等等。

使用應用於綁定的轉換器或使用 XAML 標記擴展對圖像進行預縮放。 例如：

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

如果圖像也需要主題(大多數(如果不是全部)應該),標記可以使用不同的轉換器,首先對圖像進行主題化,然後預縮放。 標記可以使用<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter><xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>或 ,具體取決於所需的轉換輸出。

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

步驟 2:確保當前 DPI 的最終大小正確。

由於 WPF 將使用在 UIElement 上設置的 BitmapScalingMode 屬性縮放當前 DPI 的 UI,因此使用預縮放影像作為其源的圖像控制項看起來將比它應該放大兩到三倍。 以下是對抗此效果的幾種方法:

- 如果知道原始圖像的尺寸為 100%,則可以指定圖像控制項的確切大小。 在應用縮放之前,這些大小將反映 UI 的大小。

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- 如果不知道原始圖像的大小,可以使用 LayoutTransform 來縮小最終圖像物件。 例如：

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>支援 WebOC
默認情況下,WebOC 控件(如 WPF 中的 Web 瀏覽器控制件或 IWebBrowser2 介面)不啟用 HDPI 檢測和支援。 結果將是一個嵌入式控制項,其顯示內容在高解析度顯示幕上太小。 下面介紹如何在特定的 Web WebOC 實例中啟用高 DPI 支援。

實作 IDocHostUIHandler 介面(請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))上的 MSDN 文章:

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

或者,實現 ICustomDoc 介面(請參閱[ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))上的 MSDN 文章:

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

將實現 IDocHostUIHandler 的類與 WebOC 的文件相關聯。 如果上述實現 ICustomDoc 介面,則一旦 WebOC 的文件屬性有效,將其轉換為 ICustomDoc 並調用 SetUIHandler 方法,傳遞實現 IDocHostUIHandler 的類。

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

如果您沒有實現 ICustomDoc 介面,則一旦 WebOC 的文件屬性有效,則需要將其強制轉換為 IOleObject,並調用`SetClientSite`該方法,傳入實現 IDocHostUIHandler 的類。 在傳遞給`GetHostInfo`方法呼叫的 DOCHOSTUIINFO 上設定DOCHOSTUIFLAG_DPI_AWARE標誌:

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

這應該是獲得 WebOC 控制以支援 HPDI 所需的全部功能。

## <a name="tips"></a>提示

1. 如果 WebOC 控件上的文檔屬性發生更改,則可能需要將文檔與 IDocHostUIHandler 類重新關聯。

2. 如果上述內容不起作用,則 WebOC 未獲取對 DPI 標誌的更改存在已知問題。 解決此問題的最可靠方法是切換 WebOC 的光學縮放,這意味著兩個調用具有兩個不同的縮放百分比值。 此外,如果需要此解決方法,則可能需要在每個導航調用上執行它。

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
