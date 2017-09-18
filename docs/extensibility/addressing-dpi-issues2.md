---
title: "定址 DPI Issues2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 處理 DPI 問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

越來越多的裝置都隨附 「 高解析度 」 畫面。 這些螢幕通常會有每英吋 \(ppi\) 超過 200 像素為單位。 使用這些電腦上的應用程式需要進行調整以符合需求的檢視裝置的一般檢視距離內容的內容。 截至 2014 年高密度的顯示畫面的主要目標是行動運算裝置 （平板電腦、 蛤殼膝上型電腦和電話）。  
  
 Windows 8.1 和更新版本包含幾項功能，讓這些機器能夠使用會顯示及環境中的機器附加於兩者適用之高密度標準密度會顯示在相同的時間。  
  
-   Windows 可以讓您將內容調整為使用 「 讓文字和其他項目放大或縮小 」 的裝置設定 （可自 Windows XP）。  
  
-   Windows 8.1 和更新版本會自動調整內容對於大部分的應用程式一致的不同像素密度的顯示器之間移動時。 當主顯示器是高密度 （200%調整），而且次要顯示標準的密度 （100%\) 時，Windows 即會自動縮小應用程式視窗內容在螢幕上顯示第二個 （1 個像素顯示每個應用程式所呈現的 4 個像素）。  
  
-   Windows 會預設為像素密度的比例，以及檢視顯示 \[\(Windows 7 和更高版本，OEM 可設定\) 的距離。  
  
-   在超過 280 ppi （如 Windows 8.1 S14\) 的新裝置上 Windows 可以自動調整 250%內容設定。  
  
 Windows 擁有處理 UI 向上擴充來充分利用增加的像素計數的方式。 應用程式選擇加入這個系統本身宣告為 「 系統 DPI 感知 」。 請不要這樣的應用程式被向上延展系統。 這會導致整個應用程式是統一的像素延伸 「 模糊 」 的使用者經驗。 例如:  
  
 ![DPI 模糊問題](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio 選擇加入的 DPI 縮放比例感知功能，並因此不 「 虛擬化。 」  
  
 Windows （和 Visual Studio） 運用數種不同方式處理縮放係數由系統設定的 UI 技術。 例如:  
  
-   WPF 會測量控制項，以與裝置無關的方式 （單位，不像素為單位）。 WPF UI，自動調整為目前的 DPI。  
  
-   不論 UI 架構的所有文字大小以點為單位，表示，因此會被系統 DPI 無關。 Win32、 WinForms 及 WPF 中的文字已相應增加正確繪製至顯示裝置時。  
  
-   Win32\/WinForms 對話方塊和視窗有啟用隨文字 – 例如，透過方格、 流程和表格版面配置面板的配置方式。 這些可讓避免字型的大小會增加時不會進行縮放的硬式編碼的像素位置。  
  
-   系統提供的圖示或系統度量資訊 （例如，SM\_CXICON 和 SM\_CXSMICON） 為基礎的資源已經是向上調整。  
  
## 較舊的 Win32 GDI \(GDI \+） 和 WinForms 為基礎的 UI  
 雖然 WPF 已經高 DPI 感知，大部分的 Win32\/GDI 基礎程式碼不原來寫入的 DPI 感知記住。 Windows 提供的 DPI 縮放比例的 Api。 建立 Win32 問題的修正程式應該使用這些一致的方式跨產品。 Visual Studio 提供的協助程式類別庫，以避免重複的功能和確保產品之間的一致性。  
  
## 高解析度的影像  
 本節主要是供開發人員延伸 Visual Studio 2013。 Visual Studio 2015 中，使用內建於 Visual Studio 映像服務。 您也可能會發現您需要支援目標許多版本的 Visual Studio，因此使用 2015年中的 \[映像服務不是可行因為不存在於舊版。 本章節也是您然後。  
  
## 向上擴充而言太小的影像  
 太小的映像可以 「 向上 」，並呈現 GDI 和 WPF 使用的一些常見方法。 受管理的 DPI helper 類別可用於內部和外部的 Visual Studio 整合人員在調整圖示、 點陣圖、 imagestrips 和 imagelists 的位址。 Win32 為基礎的原生 C \/ C \+ \+ 的協助程式可供調整 HICON、 HBITMAP、 HIMAGELIST 和 VsUI::GdiplusImage。 點陣圖的調整通常只需要一行變更之後包括 helper 程式庫的參考。 例如:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 調整 imagelist 取決於 imagelist 在載入期間，已完成，或是附加在執行階段。 如果在載入期間完成後，呼叫 LogicalToDeviceUnits\(\) imagelist 一樣點陣圖。 當程式碼需要之前撰寫的 imagelist 載入個別的點陣圖時，請務必調整影像大小的 imagelist 項目 ︰  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 原生程式碼中，維度可以調整時建立 imagelist，如下所示 ︰  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 程式庫中的函式允許指定的調整大小演算法。 當縮放影像放入 imagelists，請務必指定用於透明度，背景色彩或使用 NearestNeighbor 調整 （這會導致失真 125%和 150%）。  
  
 請參閱 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN 上的文件。  
  
 下表顯示範例的影像應該如何調整相對應的 dpi 縮放係數。 以綠色的映像表示我們從 Visual Studio 2013 （100\-200%的 DPI 縮放比例） 開始的最佳作法 ︰  
  
 ![DPI 縮放問題](~/extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## 版面配置問題  
 您可以避免常見的版面配置問題，主要是藉由調整 UI 中，相對於另一個保存點，而不是使用絕對位置 （特別是，以像素為單位）。 例如:  
  
-   版面配置\] \/ \[文字位置需要來調整向上調整影像的帳戶。  
  
-   在方格中的資料行需要調整向上調整文字的寬度。  
  
-   硬式編碼的大小或項目之間的空間也必須進行調整。 由於字型會自動向上調整，是通常沒問題，只根據文字維度的大小。  
  
 Helper 函式可用於 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> 類別，以允許在 X 和 Y 軸上縮放比例 ︰  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(函式可縮放比例，X \/ Y 軸\)  
  
-   int 空間 \= DpiHelper.LogicalToDeviceUnitsX \(10\)。  
  
-   int 高度 \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\);  
  
 有 LogicalToDeviceUnits 多載，以便調整物件，例如矩形、 點和大小。  
  
## 使用 DPIHelper 文件庫\/類別縮放影像和版面配置  
 Visual Studio DPI 協助程式庫使用原生和 managed 形式，可供 Visual Studio shell 之外的其他應用程式。  
  
 若要使用程式庫，請移至 [Visual Studio VSSDK 擴充性範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 並複製高 DPI\_Images\_Icons 範例  
  
 在原始程式檔中包含 VsUIDpiHelper.h 並呼叫 VsUI::DpiHelper 類別的靜態函式 ︰  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  請勿使用 helper 函式在模組層級或類別層級的靜態變數。 程式庫也會使用靜態執行緒同步處理，您可能會遇到順序初始化問題。 請將這些靜態變數轉換為非靜態的成員變數，或將包裝函式 （讓使用者取得第一次存取建構）。  
  
 若要從 Visual Studio 環境內執行的 managed 程式碼存取 DPI helper 函式 ︰  
  
-   使用的專案必須參考殼層 MPF 的最新版本。 例如:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   請確定專案具有參考 **System.Windows.Forms**, ，**PresentationCore**, ，和 **PresentationUI**。  
  
-   在程式碼，使用 **Microsoft.VisualStudio.PlatformUI** 的 DpiHelper 類別的命名空間和呼叫靜態函式。 支援的類型 （點、 大小、 矩形和等等），有提供擴充程式函式會傳回新的擴充物件。 例如:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## WPF 對 UI 中的映像 fuzziness 處理  
 在 WPF 中，點陣圖會自動調整大小的 WPF 目前以高品質雙立方演算法 （預設值），很適合圖片或大型的螢幕擷取畫面，但由於帶來了認知的 fuzziness 不是適當的功能表項目圖示的 DPI 縮放層級。  
  
 建議 ︰  
  
-   標誌影像及綵帶圖檔，預設值為 <xref:System.Windows.Media.BitmapScalingMode> 無法使用調整大小模式。  
  
-   功能表項目和遙控器影像 <xref:System.Windows.Media.BitmapScalingMode> 它不會造成其他扭曲成品，以消除 fuzziness （於 %200 和 300%） 時，應使用。  
  
-   •	針對大型的縮放層級不是 100%（比方說，250%或 350%） 的倍數，調整雙立方遙控器映像會導致模糊、 刷淡的 UI。 透過調整 NearestNeighbor 至 100%（例如，200%或 300%） 的最大的多個映像和雙立方從該處使用自動調整可取得更好的結果。 請參閱 \< 特殊案例 ︰ 針對大型 DPI prescaling WPF 映像的詳細資訊層級。  
  
 DpiHelper 類別 Microsoft.VisualStudio.PlatformUI 命名空間中的提供成員 <xref:System.Windows.Media.BitmapScalingMode> ，可用於繫結。 它可讓 Visual Studio shell 來控制根據 DPI 縮放比例統一，縮放模式跨產品的點陣圖。  
  
 若要使用它在 XAML 中，加入 ︰  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell 已經設定這個屬性，在最上層視窗和對話方塊。 以 WPF 為基礎的 UI，Visual Studio 中執行已繼承它。 如果設定不會傳播到特定的棋子的 UI，它可以 XAML\/WPF UI 的根項目上設定。 其中發生這種情況的地方包括 Win32 父系的項目在快顯視窗，例如 Blend 設計工具視窗執行的處理。  
  
 某些 UI 可以調整與系統設定的 DPI 縮放比例，例如 Visual Studio 文字編輯器和 WPF 架構設計人員 （WPF 桌面和 Windows 市集） 分開。 在這些情況下，不應該使用 DpiHelper.BitmapScalingMode。 若要修正此問題在編輯器中，建立自訂屬性的 IDE 小組標題為 RenderOptions.BitmapScalingMode。 HighQuality 或 NearestNeighbor 設定該屬性值，根據系統和使用者介面的組合的縮放層級。  
  
## 特殊案例 ︰ prescaling 大 DPI 層級的 WPF 映像  
 為非常大的縮放層級不是 100%（比方說，250%，350%等等） 的倍數，調整遙控器雙立方結果模糊、 刷淡的 UI 中的影像。 這些映像清晰的文字旁的印象就類似上述的光學假象。 影像看起來很接近眼睛進出相對於文字的焦點。 縮放至 100%（例如，200%或 300%） 的最大的多個與 NearestNeighbor 影像和使用雙立方的其餘部分 （額外的 50%\) 來自動調整可以改善此放大的大小調整的結果。  
  
 下列是在結果中，差異的範例的第一個影像已調整，以改善雙調整的演算法 100%\]\-\> \[200%\-\> 250%，與第二個只使用雙立方 100%\-\> 250%。  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 若要讓 UI 來使用這個雙調整，XAML 標記顯示在每個影像項目必須加以修改。 下列範例示範如何使用雙調整 WPF 中使用 DpiHelper 程式庫和 Shell.12\/14 在 Visual Studio。  
  
 步驟 1: Prescale 300%到 200%，映像等等使用 NearestNeighbor。  
  
 Prescale 使用其中一個轉換的套用繫結或 XAML 標記延伸的映像。 例如:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 如果映像也必須是佈景主題 （最，如果不是全部，應該如此），標記可以使用不同的轉換程式第一次執行的映像，然後預先調整佈景主題。 標記可以使用 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> 或 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, ，取決於所要的轉換輸出。  
  
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
  
 步驟 2 ︰ 確定最終大小是正確的目前 DPI。  
  
 因為 WPF 會針對使用 BitmapScalingMode 屬性 UIElement 上設定的目前 DPI 調整 UI，應該使用 prescaled 映像，因為其來源會尋找大於它的兩個或三次影像控制項。 以下是幾種方式來對抗這種效果 ︰  
  
-   如果您知道在 100%的原始影像的維度，您可以指定影像控制項的確切的大小。 這些大小會反映在套用之前調整 UI 的大小。  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   如果不知道原始映像的大小，LayoutTransform 可用來縮小最終映像物件。 例如:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## 啟用 WebOC HDPI 支援  
 根據預設，HDPI 偵測和支援功能，請勿啟用 WebOC 控制項 （例如在 WPF 中或 IWebBrowser2 介面 WebBrowser 控制項）。 結果會是內嵌的控制項以顯示內容在高解析度的顯示器太小。 以下說明如何啟用高 DPI 支援特定 web WebOC 執行個體。  
  
 實作 IDocHostUIHandler 介面 \(請參閱 MSDN 文件 [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) 介面\):  
  
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
  
 （選擇性） 實作 ICustomDoc 介面 \(請參閱 MSDN 文件 [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) 介面\):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 建立關聯實作 IDocHostUIHandler WebOC 文件的類別。 如果您實作上述 ICustomDoc 介面，然後 WebOC 文件屬性是有效的因為將它轉換成 ICustomDoc 並呼叫 SetUIHandler 方法，傳遞實作 IDocHostUIHandler 的類別而變更。  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 如果您並未實作 ICustomDoc 介面，則 WebOC 文件屬性是有效的因為您必須將它轉換成 IOleObject，並呼叫 SetClientSite 方法，在類別中實作 IDocHostUIHandler 傳遞。 設定傳遞至 GetHostInfo 方法呼叫 DOCHOSTUIINFO DOCHOSTUIFLAG\_DPI\_AWARE 旗標 ︰  
  
```c#  
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
  
## 祕訣  
  
1.  如果 WebOC 控制項上的文件屬性變更時，您可能需要將文件與 IDocHostUIHandler 類別重新關聯。  
  
2.  如果上述程式碼無法運作，但沒有不收取 DPI 旗標變更 WebOC 的已知的問題。 切換 WebOC，意義與兩個不同的縮放百分比值的兩個呼叫視覺化縮放為解決此問題最可靠的方式。 此外，如果需要此因應措施，可能需要在每次瀏覽執行它。  
  
    ```c#  
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