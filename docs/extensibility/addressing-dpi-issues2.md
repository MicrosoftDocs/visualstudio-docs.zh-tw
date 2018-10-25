---
title: 定址 DPI Issues2 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c4ca03c932b86ad6f9907020b037abb1308a6f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918528"
---
# <a name="address-dpi-issues"></a>處理 DPI 問題
越來越多的裝置都隨附 「 高解析度 」 畫面。 這些畫面通常會有超過 200 個像素為單位，每英吋 (ppi)。 使用這些電腦上的應用程式需要相應增加以符合檢視裝置的一般檢視距離內容需求的內容。 自 2014年起，高密度顯示的主要目標是行動運算裝置 （平板電腦、 蛤殼膝上型電腦和手機）。  
  
 Windows 8.1 和更新版本包含數個功能，讓這些機器能夠使用的顯示和及環境中將機器附加至同時適用之高密度標準密度會顯示在相同的時間。  
  
- Windows 可以讓您將內容調整成使用 「 讓文字和其他項目放大或縮小 」 的裝置設定 （可自 Windows XP）。  
  
- Windows 8.1 和更新版本會自動將內容調整對於大部分的應用程式一致的不同像素密度的顯示器之間移動時。 Windows 上的次要顯示器，當主要的顯示是高密度 （200%調整），而且次要顯示標準密度 （100%) 時，自動相應減少應用程式視窗內容 (針對每個所呈現的 4 個像素顯示的 1 個像素應用程式）。  
  
- Windows 會預設為像素密度的比例，以及檢視顯示 (Windows 7 及更新版本，OEM 可設定) 的距離的權限。  
  
- 在超過 280 ppi （從 Windows 8.1 S14) 的新裝置上 Windows 可以自動調整設定為 250%內容。  
  
  Windows 具有處理向上調整 UI 的方式，利用增加的像素計數。 應用程式選擇加入此系統本身宣告為 「 系統 DPI 感知 」。 請不要這樣的應用程式系統相應增加。 這會導致整個應用程式是一致的像素延伸了 「 模糊 」 的使用者體驗。 例如:   
  
  ![DPI 問題模糊](../extensibility/media/dpi-issues-fuzzy.png "DPI 問題模糊")  
  
  Visual Studio 中選擇要 DPI 縮放比例感知，並因此未 「 虛擬化。 」  
  
  Windows （和 Visual Studio） 運用數種不同方式處理縮放係數由系統設定的 UI 技術。 例如:   
  
- WPF 會測量控制項，以與裝置無關的方式 （單位，不像素為單位）。 WPF UI 會自動調整為目前的 DPI。  
  
- 不論 UI 架構的所有文字大小以點表示，因此會被系統 DPI 獨立。 Win32、 WinForms 和 WPF 中的文字已相應增加正確繪製至顯示裝置時。  
  
- Win32/WinForms 對話方塊和視窗有啟用文字 （例如，透過方格、 流程和表格版面配置面板） 調整大小的版面配置的方式。 這些可讓避免字型的大小會增加時不會進行縮放的硬式編碼的像素位置。  
  
- 系統所提供的圖示或系統計量 （例如 SM_CXICON 和 SM_CXSMICON） 為基礎的資源已相應增加。  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>較舊的 Win32 GDI (GDI +） 和 WinForms 為基礎的 UI  
 在 WPF 高 DPI 感知，Win32/GDI 式程式碼大多不原始寫入的記住 DPI 感知。 Windows 提供的 DPI 縮放比例的 Api。 Win32 問題的修正程式應該使用這些在產品內以一致的方式。 Visual Studio 提供的協助程式類別庫，以避免複製功能，並確保在產品內的一致性。  
  
## <a name="high-resolution-images"></a>高解析度的映像  
 本節主要是供開發人員延伸 Visual Studio 2013。 Visual Studio 2015 中，使用內建於 Visual Studio 映像服務。 您可能也會發現您需要支援/目標的 Visual Studio 的許多版本，因此使用 2015年中的 映像服務不是選項因為不存在於舊版。 本章節也是您然後。  
  
## <a name="scaling-up-images-that-are-too-small"></a>相應增加太小的映像  
 太小的映像可以相應增加，並呈現 GDI 和 WPF 使用的一些常見方法。 受管理的 DPI 協助程式類別可用於內部和外部的 Visual Studio 整合人員在調整圖示、 點陣圖、 imagestrips 和 imagelists 的位址。 Win32 原生 C / C + + 的協助程式可供調整 HICON、 HBITMAP、 HIMAGELIST 和 VsUI::GdiplusImage。 縮放點陣圖的比例通常只需要一行變更之後包含協助程式程式庫的參考。 例如:   
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 調整映象清單取決於 imagelist 是否在載入期間，已完成，或附加在執行階段。 如果是完成在載入時，呼叫`LogicalToDeviceUnits()`與您 imagelist 會點陣圖。 當程式碼需要之前撰寫的 imagelist 載入個別的點陣圖時，請務必調整影像大小的 imagelist 項目：  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 在原生程式碼中，維度可以調整，如下所示建立 imagelist 時：  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 文件庫中的函式允許指定的調整大小的演算法。 當調整映像放入 imagelists，請務必指定用於透明度的背景色彩，或使用 NearestNeighbor 縮放比例 （這會導致在 125%和 150%的扭曲）。  
  
 請參閱<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN 上的文件。  
  
 下表顯示範例的影像應該如何縮放以相對應的 DPI 縮放係數。 橘色中簡述的映像表示自 （100-200%的 DPI 縮放比例） 的 Visual Studio 2013 起我們最佳做法：  
  
 ![DPI 縮放問題](../extensibility/media/dpi-issues-scaling.png "DPI 縮放問題")  
  
## <a name="layout-issues"></a>版面配置問題  
 您可以避免常見的版面配置問題，主要是由相應的 UI 中，而另一個是相對於保留點，而不是使用絕對位置 （具體而言，單位為像素）。 例如:   
  
- 版面配置] / [文字位置需要調整相應增加映像的帳戶。  
  
- 在方格中的資料行必須能夠調整相應增加文字的寬度。  
  
- 硬式編碼的大小或項目之間的空間也會需要相應增加。 因為字型自動相應增加，是通常沒問題，只根據文字維度的大小。  
  
  Helper 函式可用於<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>若要允許縮放 X 和 Y 軸上的類別：  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (函式允許調整 X / Y 軸)  
  
- int 空間 = DpiHelper.LogicalToDeviceUnitsX (10);  
  
- int 高度 = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
  有 LogicalToDeviceUnits 多載，若要允許縮放物件，例如矩形、 點和大小。  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>使用 「 DPIHelper 程式庫/類別縮放影像和版面配置  
 Visual Studio DPI 協助程式程式庫提供原生和 managed 表單，並可供外部使用 Visual Studio shell 的其他應用程式。  
  
 若要使用的程式庫，請前往[Visual Studio VSSDK 擴充性範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)並複製高 DPI_Images_Icons 範例。  
  
 原始程式檔中包含*VsUIDpiHelper.h*呼叫的靜態函式和`VsUI::DpiHelper`類別：  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  請勿在模組層級或類別層級的靜態變數使用 helper 函式。 程式庫也會使用靜態執行緒同步處理，您可能會遇到的問題順序初始化。 請將這些靜態變數轉換成非靜態成員變數，或將包裝函式，因此它們取得建構在第一次存取上）。  
  
 若要從 Visual Studio 環境內執行的 managed 程式碼存取 DPI helper 函式：  
  
-   取用專案必須參考殼層 MPF 的最新版本。 例如:   
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   請確定專案具有參考**System.Windows.Forms**， **PresentationCore**，並**PresentationUI**。  
  
-   在程式碼，使用**Microsoft.VisualStudio.PlatformUI** DpiHelper 類別的命名空間和呼叫靜態函式。 支援的類型 （點、 大小、 矩形和等等），都有提供擴充程式函式會傳回新的擴充物件。 例如:   
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>使用 WPF 對 UI 中的映像模糊不清的處理  
 在 WPF 中，點陣圖會自動調整大小的 WPF 目前使用高品質的雙立方演算法 （預設值），這非常適用於圖片或大型的螢幕擷取畫面，但因為它會導致模糊不清察覺到不是適當的功能表項目圖示的 DPI 縮放層級.  
  
 建議：  
  
- 標誌影像及橫幅插圖，預設值為<xref:System.Windows.Media.BitmapScalingMode>無法使用調整大小模式。  
  
- 功能表項目和遙控器映像，<xref:System.Windows.Media.BitmapScalingMode>它不會造成其他扭曲成品，以避免模糊不清 （在 200%到 300%） 時，應使用。  
  
- 大型的縮放層級不是 100%（比方說，250%或 350%） 的倍數，調整具有雙立方的遙控器映像會導致模糊、 刷淡的 UI。 透過第一個調整 NearestNeighbor 至 100%（例如，200%或 300%） 的最大的多個映像和雙立方從中使用自動調整規模可取得更佳的結果。 請參閱 < 特殊案例︰ 適用於大型的 DPI prescaling WPF 映像的詳細資訊層級。  
  
  DpiHelper Microsoft.VisualStudio.PlatformUI 命名空間中的類別提供成員<xref:System.Windows.Media.BitmapScalingMode>，可用來繫結。 它可讓 Visual Studio shell 來控制的 DPI 縮放比例根據一致的方式，調整模式在產品內的點陣圖。  
  
  若要使用它在 XAML 中，加入：  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell 已經設定這個屬性，在最上層視窗和對話方塊。 WPF 為基礎的 UI，在 Visual Studio 中執行已繼承它。 如果設定不會傳播至 UI 的特定棋子，它可以在 XAML/WPF UI 的根項目上設定。 其中發生這種情況的地方包含 Win32 父系的項目在快顯視窗，例如 Blend 設計工具的 windows 執行的處理。  
  
 某些 UI 可以調整獨立的系統設定 DPI 縮放層級，例如 Visual Studio 文字編輯器和 WPF 架構設計人員 （WPF 桌面和 Windows 市集）。 在這些情況下，不應該使用 DpiHelper.BitmapScalingMode。 若要修正此問題在編輯器中，IDE 小組建立自訂的屬性標題為 RenderOptions.BitmapScalingMode。 將該屬性值設 HighQuality 或 NearestNeighbor 根據合併的縮放層級系統與您的 UI。  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>特殊案例： prescaling 大型 DPI 層級的 WPF 映像  
 不是 100%（比方說，250%，350%等等） 的倍數的非常大型的縮放層級，縮放比例模糊、 刷淡的 UI 中的雙立方結果遙控器映像。 這些映像，務求文字旁的印象，幾乎就像光學視覺效果的。 映像似乎較近的眼睛及移出相對於文字的焦點。 在此放的大小調整的結果便可改善第一次 NearestNeighbor 至 100%（例如，200%或 300%） 的最大的多個映像以及調整與雙立方至其餘部分 （額外的 50%)。  
  
 以下是範例中的差異，在結果中，第一個影像會縮放，以改善雙精度浮點數調整的演算法 100%]-> [200%-> 250%與第二個只是使用雙立方 100%]-> [250%。  
  
 ![DPI 問題 Double 縮放的範例](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 問題 Double 縮放的範例")  
  
 若要讓 UI，以用於這個雙精度浮點數調整，XAML 標記，顯示每個影像項目將會需要修改。 下列範例示範如何使用 使用 DpiHelper 程式庫和 Shell.12/14 的 Visual Studio 中的 在 WPF 中調整雙精度浮點數。  
  
 步驟 1: 300 %prescale 為 200%的映像等等使用 NearestNeighbor。  
  
 Prescale 使用任一個套用的繫結，或使用 XAML 標記延伸的轉換子的映像。 例如:   
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 如果映像也需要設定佈景主題 （最，如果不是全部，應該如此），標記就可以使用不同的轉換程式第一次執行的映像，然後預先調整的佈景主題。 標記可以使用任何一種<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter>或<xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>，取決於所需的轉換輸出。  
  
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
  
 步驟 2： 確定最終的大小是正確的目前 DPI。  
  
 因為 WPF 會針對目前使用 BitmapScalingMode 屬性集的 UIElement 上的 DPI 縮放 UI，使用 prescaled 映像，因為其來源會尋找兩個或三倍大比影像控制項應該。 以下是幾種方式來應付這種效果：  
  
-   如果您知道原始的映像，在 100%的維度，您可以指定確切的大小的影像控制項。 這些大小將會反映在套用之前調整 UI 的大小。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   如果不知道原始映像的大小，LayoutTransform 可用來相應減少為最終的映像物件。 例如:   
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>啟用以 WebOC 的 HDPI 支援  
 根據預設，HDPI 偵測和支援功能，請勿啟用 WebOC 控制項 （例如在 WPF 中或 IWebBrowser2 介面 WebBrowser 控制項）。 結果會是內嵌的控制項與太小而高解析度的顯示器上顯示內容。 以下說明如何啟用特定 web WebOC 執行個體的高 DPI 支援。  
  
 實作 IDocHostUIHandler 介面 (請參閱 MSDN 文章[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):  
  
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
  
 （選擇性） 實作 ICustomDoc 介面 (請參閱 MSDN 文章[ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 建立關聯之類別的實作 IDocHostUIHandler WebOC 的文件。 如果您實作上述 ICustomDoc 介面，然後只要 WebOC 的文件屬性是有效的將它轉換成 ICustomDoc 並呼叫 SetUIHandler; 方法，傳遞可實作 IDocHostUIHandler 類別而變更。  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 如果您未實作 ICustomDoc 介面，則只要 WebOC 的文件屬性是有效的您必須將它轉換成 IOleObject，並呼叫`SetClientSite`方法並傳入實作 IDocHostUIHandler 的類別。 設定傳遞至 DOCHOSTUIINFO DOCHOSTUIFLAG_DPI_AWARE 旗標`GetHostInfo`方法呼叫：  
  
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
  
1.  如果 WebOC 控制項上的文件屬性變更時，您可能需要重新關聯 IDocHostUIHandler 類別的文件。  
  
2.  如果上述無法運作，則不會收取 DPI 旗標變更 WebOC 的已知的問題。 修正此問題的最可靠方式是切換 WebOC，包含兩個不同的縮放百分比值的意義兩次呼叫視覺化縮放。 此外，如果需要此因應措施，它可能需要對每個巡覽呼叫。  
  
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
