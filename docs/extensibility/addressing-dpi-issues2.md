---
title: "定址 DPI Issues2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e944c8a998a3e8bba46d5018faf1b9103a91240
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="addressing-dpi-issues"></a>定址 DPI 問題
越來越多的裝置所傳送與 「 高解析度 」 畫面。 這些畫面通常會有每英吋點數 (ppi) 超過 200 像素為單位。 必須搭配使用這些電腦上的應用程式內容延伸到檢視裝置的正常檢視距離內容的需求。 顯示適用之高密度的主要目標 2014 中，為行動運算裝置 （平板電腦、 蛤殼膝上型電腦和手機）。  
  
 Windows 8.1 和更新版本包含數個功能，讓這些機器以搭配顯示和機器連接兩者都適用之高密度且標準密度會顯示在同一時間的環境。  
  
-   Windows 可以讓您使用 「 讓文字和其他項目放大或縮小 」 的裝置將內容設定 （適用 Windows xp）。  
  
-   Windows 8.1 和更新版本自動縮放表單內容對於大部分的應用程式一致的不同像素密度的顯示器之間移動時。 Windows 次要顯示器上，當主要顯示較高的密度 （200%調整），而次要顯示標準密度 （100%) 時，自動縮放應用程式視窗內容 (針對每個所呈現的 4 個像素顯示的 1 個像素應用程式）。  
  
-   Windows 會預設為像素密度的比例，以及檢視距離的顯示 (Windows 7 及更新版本，OEM 可設定) 的權限。  
  
-   Windows 可以自動將內容調整向上 250%超過 280 ppi (as of Windows 8.1 S14) 的新裝置上。  
  
 Windows 具有處理向上擴充 UI 的方式，利用增加的像素的計數。 應用程式選擇加入這個系統藉由宣告本身的 「 系統 DPI 感知 」。 系統會調整不要這樣的應用程式。 這會導致整個應用程式是統一的像素延展的 「 模糊 」 的使用者體驗。 例如:   
  
 ![DPI 發出模糊](../extensibility/media/dpi-issues-fuzzy.png "DPI 發出模糊")  
  
 Visual Studio 選擇加入的 DPI 縮放比例感知，並因此不 「 虛擬化。 」  
  
 Windows （和 Visual Studio） 利用數種具有不同的方法可處理調整係數由系統設定的 UI 技術。 例如:   
  
-   WPF 會測量控制項，以與裝置無關的方式 （單位，不像素為單位）。 WPF UI 自動調整為目前的 DPI。  
  
-   不論使用者介面架構的所有文字大小以點為單位，表示，並因此會被系統 DPI 無關。 Win32、 WinForms 及 WPF 文字已經向上延展正確繪製至顯示裝置時。  
  
-   Win32/WinForms 對話方塊和視窗有啟用隨文字-例如，透過方格、 流程和資料表的版面配置面板的版面配置方式。 這些可讓避免字型的大小會增加時不會進行縮放的硬式編碼的像素位置。  
  
-   系統提供的圖示或資源 （例如，SM_CXICON 和 SM_CXSMICON） 的系統標準為基礎，已經擴充規模。  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>較舊的 Win32 GDI (GDI +） 和 WinForms 為基礎的 UI  
 雖然 WPF 已經在高 DPI 感知，大部分的 Win32/GDI 為基礎的程式碼不原來寫入的 DPI 感知記住。 Windows 提供的 DPI 縮放比例的 Api。 Win32 問題的修正程式應該使用它們持續跨產品。 Visual Studio 提供的協助程式類別庫，以避免複製功能，並確保產品之間的一致性。  
  
## <a name="high-resolution-images"></a>高解析度的影像  
 此區段是主要用於擴充 Visual Studio 2013 開發人員。 Visual Studio 2015 中，使用內建在 Visual Studio 映像服務。 您也可能會發現您需要支援目標許多版本的 Visual Studio，因此使用 2015年中的 映像服務不是可行因為它不存在先前的版本。 本章節也是您然後。  
  
## <a name="scaling-up-images-that-are-too-small"></a>向上擴充太小的影像  
 可以 「 向上 」 並呈現在 GDI 和使用的一些常見方法的 WPF 太小的映像。 受管理的 DPI 協助程式類別可用來調整圖示、 點陣圖、 imagestrips 和 imagelists 位址的內部和外部 Visual Studio 整合者。 Win32 原生 C / C + + 的協助程式可供 HICON、 HBITMAP、 HIMAGELIST 和 VsUI::GdiplusImage 縮放比例。 通常點陣圖的縮放只需要一行變更之後包括 helper 程式庫的參考。 例如:   
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 調整 imagelist 取決於 imagelist 在載入期間，已完成，或是將會附加在執行階段。 如果在載入時間完成，呼叫 LogicalToDeviceUnits() 使用 imagelist 一樣點陣圖。 當程式碼需要先撰寫 imagelist 載入個別的點陣圖時，請確定調整 imagelist 的映像大小：  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 原生程式碼中，維度可以縮放時建立 imagelist，如下所示：  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 文件庫中的函式可讓指定的調整大小的演算法。 當縮放影像放入 imagelists，請務必指定透明度、 使用的背景色彩，或使用 NearestNeighbor 縮放比例 （這會導致在 125%和 150%失真）。  
  
 請參閱<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN 上的文件。  
  
 下表顯示範例的影像應該如何縮放相對應的 dpi 縮放比例因素。 映像以綠色代表我們於 Visual Studio 2013 （100-200 %dpi 縮放比例） 的最佳作法：  
  
 ![DPI 縮放問題](../extensibility/media/dpi-issues-scaling.png "DPI 縮放問題")  
  
## <a name="layout-issues"></a>版面配置問題  
 主要是藉由調整 UI 中，而另一個是相對於保持點，而不是使用絕對位置 （特別是，以像素單位表示），您可以避免常見的版面配置問題。 例如:   
  
-   版面配置] / [文字位置需要調整相應映像的帳戶。  
  
-   在方格中的資料行必須具有寬度調整相應的文字。  
  
-   硬式編碼的大小或項目之間的空間將也需要擴充規模。 因為字型自動縮放，是通常沒問題，只根據文字維度的大小。  
  
 Helper 函式可用於<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>允許 X 和 Y 軸上縮放比例類別：  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (函式可讓縮放比例，X / Y 軸)  
  
-   int 空間 = DpiHelper.LogicalToDeviceUnitsX (10)。  
  
-   int 高度 = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 有 LogicalToDeviceUnits 多載，可以讓擴充物件，例如矩形、 點和大小。  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>使用 DPIHelper 程式庫/類別縮放影像及版面配置  
 Visual Studio DPI 協助程式程式庫使用原生和 managed 表單中，可以使用 Visual Studio shell，由其他應用程式。  
  
 若要使用文件庫，請移至[Visual Studio VSSDK 擴充性範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)並複製到高 DPI_Images_Icons 範例  
  
 原始程式檔中包含 VsUIDpiHelper.h 並呼叫 VsUI::DpiHelper 類別的靜態函式：  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  請勿在模組層級或類別層級的靜態變數使用 helper 函式。 程式庫也會使用靜態變數進行執行緒同步處理，您可能會遇到的問題順序初始化。 請將這些靜態變數轉換成非靜態的成員變數，或將包裝函式 （讓他們取得建構在第一次存取上）。  
  
 若要從 Visual Studio 環境內執行的 managed 程式碼存取 DPI helper 函式：  
  
-   使用的專案必須參考殼層 MPF 的最新版本。 例如:   
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   請確定專案具有參考**System.Windows.Forms**， **PresentationCore**，和**PresentationUI**。  
  
-   在程式碼，使用**Microsoft.VisualStudio.PlatformUI** DpiHelper 類別的命名空間和呼叫靜態函式。 支援的類型 （點、 大小、 矩形和等等），都有提供擴充函式會傳回新的擴充物件。 例如:   
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>將 UI 中的 WPF 映像模糊不清處理  
 在 WPF 中，點陣圖會自動調整其大小 wpf 目前以高品質雙立方演算法 （預設值），很適合圖片或大型的螢幕擷取畫面，但由於帶來了認知的模糊不清不是適當的功能表項目圖示的 DPI 縮放層級.  
  
 建議：  
  
-   標誌影像與橫幅作品，預設值為<xref:System.Windows.Media.BitmapScalingMode>無法使用調整大小模式。  
  
-   功能表項目和遙控器影像<xref:System.Windows.Media.BitmapScalingMode>它並不會造成其他扭曲成品，以避免模糊不清 （於 %200 和 300%） 時，應使用。  
  
-   針對大型縮放層級不是 100%（例如，250%或 %350） 的倍數，與雙立方的遙控器影像縮放比例會導致模糊、 刷淡的 UI。 縮放為 100%（例如，%200 或 300%） 的最大的多個與 NearestNeighbor 影像並調整雙立方從該處取得更好的結果。 請參閱 特殊案例： 適用於大型 DPI prescaling WPF 映像如需詳細資訊層級。  
  
 Microsoft.VisualStudio.PlatformUI 命名空間中的 DpiHelper 類別提供成員<xref:System.Windows.Media.BitmapScalingMode>，可以用於繫結。 它可讓 Visual Studio shell 來控制模式在調整產品一致的方式，根據 DPI 縮放比例的點陣圖。  
  
 若要在 XAML 中使用它，加入：  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell 已經設定這個屬性在最上層的視窗和對話方塊。 WPF 為基礎的 UI，Visual Studio 中執行已繼承它。 如果設定不會傳播給特定的棋子的 UI，所以可以在 XAML/WPF UI 的根項目上設定。 其中發生這種情況的地方包括 Win32 父系的項目在快顯視窗，以及設計出一次執行的 windows 處理序，（例如 Blend）。  
  
 某些 UI 可以調整獨立的系統組 DPI 縮放層級，例如 Visual Studio 文字編輯器和以 WPF 為基礎設計工具 （WPF 桌面和 Windows 市集）。 在這些情況下，不應該使用 DpiHelper.BitmapScalingMode。 若要修正此問題在編輯器中，IDE 小組建立自訂的屬性標題為 RenderOptions.BitmapScalingMode。 該屬性值設定為 HighQuality 或 NearestNeighbor 根據合併的縮放層級的系統，您的 UI。  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊情況： prescaling 大型 DPI 層級的 WPF 映像  
 不是 100%（例如，250%、 350%等等） 的倍數的非常大型的縮放層級，縮放比例遙控器雙立方結果模糊、 刷淡的 UI 中的影像。 這些映像清晰文字旁的印象就類似上述光學幻影。 影像看起來像是接近眼睛與失焦相對於文字。 縮放為 100%（例如，%200 或 300%） 的最大的多個與 NearestNeighbor 影像和調整雙立方其餘 （非其他的 50%) 可以改善這個放大的大小調整的結果。  
  
 以下是範例的差異，在結果中，其中的第一個影像會調整 200%-250%>]-> [100%的改善雙調整演算法與第二個只是具有雙立方 100%-250%。  
  
 ![DPI 發出的縮放比例的 Double 範例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 發出的縮放比例的 Double 範例")  
  
 若要讓 UI，使用此雙縮放比例，XAML 標記顯示在每個影像項目將會需要修改。 下列範例會示範如何使用雙縮放比例在 WPF 中使用 DpiHelper 程式庫和 Shell.12/14 的 Visual Studio 中。  
  
 步驟 1: Prescale 300%到 200%的映像，並以此類推使用 NearestNeighbor。  
  
 Prescale 使用任一套用繫結，或使用 XAML 標記延伸的轉換子的映像。 例如:   
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 如果映像也需要設定佈景主題 （最，如果不是全部，應），標記就可以使用不同的轉換子的第一次的映像，然後預先調整佈景主題。 標記可以使用<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>或<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>，視所要的轉換輸出。  
  
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
  
 步驟 2： 確定最終大小是正確的目前 DPI。  
  
 因為 WPF 將適用於目前使用 BitmapScalingMode 屬性集 uielement 的 DPI 縮放 UI，應該使用 prescaled 映像，因為它的來源會尋找大於它的兩個或三個時間影像控制項。 以下是幾種方式計數器這個效果：  
  
-   如果您知道在 100%的原始影像的維度，您可以指定影像控制項的確切的大小。 這些大小會反映調整之前，先 UI 的大小時會套用。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   如果不知道原始映像的大小，LayoutTransform 可用以調降最終映像物件。 例如:   
  
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
 根據預設，HDPI 偵測和支援功能，請勿啟用 WebOC 控制項 （例如 WPF 或 IWebBrowser2 介面中的 WebBrowser 控制項）。 結果會內嵌為太小而高解析度的顯示器上顯示內容控制項。 以下描述如何啟用高 DPI 支援特定 web WebOC 執行個體。  
  
 實作 IDocHostUIHandler 介面 (請參閱 MSDN 文件[IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx)介面):  
  
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
  
 （選擇性） 實作 ICustomDoc 介面 (請參閱 MSDN 文件[ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx)介面):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 建立關聯之類別的實作 IDocHostUIHandler WebOC 文件。 如果您實作上述 ICustomDoc 介面，然後只要 WebOC 文件屬性是有效的將它轉換成 ICustomDoc 並呼叫 SetUIHandler 方法，傳遞實作 IDocHostUIHandler 的類別而變更。  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 如果並未實作 ICustomDoc 介面，則 WebOC 文件屬性是有效的因為您必須將它轉換成 IOleObject，並呼叫 SetClientSite 方法，傳入實作 IDocHostUIHandler 的類別。 設定傳遞至 GetHostInfo 方法呼叫 DOCHOSTUIINFO DOCHOSTUIFLAG_DPI_AWARE 旗標：  
  
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
  
 這應該是所有您需要取得 WebOC 控制項支援 HPDI。  
  
## <a name="tips"></a>秘訣  
  
1.  如果 WebOC 控制項上的文件屬性變更時，您可能需要重新關聯 IDocHostUIHandler 類別文件。  
  
2.  如果上述無法運作，但沒有不收取 DPI 旗標，變更 WebOC 的已知的問題。 修正這最可靠方式就是切換 WebOC，包含兩個不同的縮放百分比的值表示兩個呼叫光學縮放。 此外，如果需要此因應措施，可能需要執行每一次瀏覽呼叫。  
  
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