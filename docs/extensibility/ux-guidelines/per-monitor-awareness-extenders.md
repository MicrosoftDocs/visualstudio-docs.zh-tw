---
title: Visual Studio 的擴充項的個別監視器感知支援
titleSuffix: ''
description: 深入了解新的擴充性支援，針對每個監視-感知用於 Visual Studio 2019。
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477683"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio 的擴充項的個別監視器感知支援

在 Visual Studio 2019 之前的版本有 DPI 感知上下文會設定為系統感知的功能，而不是個別監視器 DPI 感知 (PMA)。 知悉產生的系統中執行降級的視覺效果 （例如模糊的字型或圖示） 中每次 Visual Studio 必須跨不同的縮放比例的監視器呈現或機器使用不同的顯示器組態 （例如不同的遠端登入Windows 調整)。

Visual Studio 2019 的 DPI 感知內容是做為個別監視器感知能力，讓 Visual Studio，來呈現根據顯示其裝載所在的組態集，而不是一般的系統定義的組態。 最終轉譯務求 UI 的實作 PMA 支援的介面區。

請參閱[高 DPI 桌面應用程式在 Windows 上開發](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)本文件涵蓋的條款及整體案例的詳細資訊的文件。

## <a name="quickstart"></a>快速入門
- 請確定 Visual Studio 正在執行中 PMA 模式 (請參閱**啟用 PMA**)

- 正確驗證您的擴充功能運作方式，跨一組常見的案例 (請參閱**測試您的擴充功能的 PMA 問題**)

- 如果您發現問題時，您將需要新增新的 PMA nuget 套件，診斷和使用的策略與本文所討論的建議修正問題

## <a name="enabling-pma"></a>啟用 PMA
若要啟用 Visual Studio 中的 PMA，必須符合下列需求：
1)  Windows 10 April 2018 Update (v1803 RS4) 或更新版本
2)  .NET framework 4.8 RTM 或更新版本 (目前為獨立預覽或新的套件組合的隨附 Windows Insider 組建）
3)  使用 visual Studio 2019 [「 適用於具有不同像素密度的螢幕最佳化轉譯"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019)啟用選項

一旦符合這些需求時，Visual Studio 會自動啟用 PMA 跨處理序。

## <a name="testing-your-extensions-for-pma-issues"></a>測試您的擴充功能的 PMA 問題

Visual Studio 正式支援 WPF、 Windows Form、 microsoft、excel、win32 及 HTML/JS UI 架構。 當 Visual Studio 會放入 PMA 模式中時，不同的 UI 堆疊行為不同。 因此，不論 UI 架構，建議執行測試時，是為了要確保所有 UI 都會遵守 PMA。

不論 UI 架構擴充功能支援，建議您驗證下列常見案例：

1. 在應用程式時執行 * 變更單一監視器環境的縮放比例
    - 此案例可協助測試到 UI 動態的 Windows DPI 變更回應

2. 應用程式執行時，停駐/卸除之連接的監視設定為主要工作和連結的監視器膝上型電腦有不同的縮放比例，低於主要複本。
    - 此案例可協助測試 UI 會回應至顯示 DPI 變更，以及以動態方式處理顯示要加入或移除

3. 擁有多個具有不同的縮放比例的監視器，而且它們之間移動應用程式。
    - 此案例可協助測試顯示 DPI 變更，正在回應 UI
    
4. 遠端處理到機器當本機和遠端電腦的主要監視器有不同的縮放比例。
    - 此案例可協助測試到 UI 動態的 Windows DPI 變更回應

UI 是否可能有問題的良好初步測試是程式碼是否使用其中一個*Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*或*Microsoft.VisualStudio.PlatformUI.DpiHelper*類別。 這些舊的 DpiHelper 類別僅支援系統 DPI 感知，而且不一定正確運作 PMA 程序時。

這些 DpiHelpers 的典型用法看起來像：

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

在上述範例中，表示視窗的邏輯界限的矩形會轉換成裝置單位，以便將它傳遞至原生方法 MonitorFromPoint 預期裝置座標，以傳回精確的監視器指標。

### <a name="classes-of-issues"></a>類別的問題

適用於 Visual Studio 啟用 PMA 時，UI，導致數個常見的方式複寫問題。 最，如果不是全部，這些問題可能會發生在任何 Visual Studio 支援的 UI 架構。 此外，這些問題可能會發生甚至當 UI 的一段裝載混合式 DPI 縮放比例的案例中 (請參閱 Windows[文件](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)若要了解更多)。 

#### <a name="win32-window-creation"></a>建立 Win32 視窗
使用建立時 windows CreateWindow() 或 CreateWindowEx()，常見的模式是建立視窗在座標 0，0 （主顯示器的左上角），然後移動到其最終位置。 不過，這麼做可以讓視窗觸發程序的 DPI 變更訊息或事件，它可以重新觸發其他 UI 訊息或事件，並最終會導致不想要的行為或轉譯。

#### <a name="wpf-element-placement"></a>WPF 項目位置
當您移動使用舊的 Microsoft.VisualStudio.Utilities.Dpi.DpiHelper 的 WPF 項目，左上角座標可能不正確地計算時項目是在非主要 DPI 的情況下。

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>序列化的 UI 項目大小或位置
每當它儲存在不同的 DPI 內容在還原 UI 大小或位置，它會定位和調整大小不正確。 這是視窗的因為邏輯界限會轉換成裝置單位上，以便將它傳遞至 Win32 方法 MonitorFromPoint 預期裝置座標，以傳回精確的監視器指標。

#### <a name="incorrect-scaling"></a>不正確的縮放比例
但當移動至不同 DPI 的顯示器時，它們不重新調整，因此，最後是太大或太小，其內容時，會正確，調整主要 DPI 上建立的 UI 項目。

#### <a name="incorrect-bounding"></a>不正確的週框
同樣地，若要調整的問題，UI 項目會計算正確地在其主要的 DPI 內容，其界限但移至非主要 DPI 時，它們不會正確計算新的界限。 因此，內容的視窗最後會太小或太大，相較於主機的 UI 中，導致空白空間或裁剪。

#### <a name="drag--drop"></a>拖放
每當在混合式 DPI 案例 （例如不同 UI 項目呈現在主要和非主要 DPI 內容中）、 拖放座標可能是便常常，最終的置放位置結束設定不正確所導致。

#### <a name="out-of-process-ui"></a>跨處理序 UI
某些 UI 建立跨處理序，並建立外部程序是否在不同 DPI 感知的模式比 Visual Studio 中，這會導致任何先前的轉譯問題。

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Windows Form 控制項、 影像或未顯示的 windows
此問題的主要原因之一是嘗試重設父代的控制項或一個 DpiAwarenessContext 到不同的 DpiAwarenessContext 視窗與視窗的開發人員。 

下圖顯示在視窗的父代之目前的 Windows 作業系統限制，除非明確地變更裝載行為的執行緒：

![正確的父代行為的螢幕擷取畫面](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

如此一來，如果您將不受支援的模式之間的父子式關聯性時，它將會失敗，並控制或視窗可能不會如預期般轉譯。

### <a name="diagnosing-issues"></a>診斷問題
有許多因素需要考量識別 PMA 相關問題時： 

1. 沒有 UI 或預期的 API 邏輯或裝置的值。
    - WPF UI 和 Api 通常會使用邏輯值 （但不是一定）
    - Win32 UI 和 Api 通常會使用裝置的值

2. 值來自何處？
    - 如果從其他 UI 或 API 收到的值時，是它傳遞裝置或邏輯值。
    - 如果多個來源接收值，它們全都使用/期望相同類型的值還是轉換需要混搭嗎？

3. 使用中的 UI 常數和它們在何種形式是？

4. 是的執行緒中的值正確的 DPI 內容接收嗎？
    - 若要啟用 CLMM 變更通常應該將程式碼路徑放在正確的內容，不過，外部的主要訊息迴圈或事件流程完成的工作可能會以錯誤的 DPI 內容中執行。

5. 值進行交叉 DPI 內容界限嗎？
    - 拖放在一般狀況的座標可以與 DPI 內容的位置。 視窗中嘗試執行正確的作業，但在某些情況下，主應用程式 UI 可能需要執行轉換工作，以確保相符的內容界限。

### <a name="pma-nugget-package"></a>PMA Nuget 封裝
新的 DpiAwarness 程式庫都位於 Microsoft.VisualStudio.DpiAwareness NuGet 套件。

### <a name="recommended-tools"></a>建議的工具
下列工具可協助您跨一些不同的 UI 堆疊支援 Visual Studio 偵錯 PMA 相關問題。

#### <a name="snoop"></a>窺探
Snoop 是 XAML 的偵錯工具具有內建的 Visual Studio XAML 工具不會有一些額外功能。 此外，Snoop 不需要主動偵錯 Visual Studio 能夠檢視和調整其 WPF UI。 Snoop 可用於診斷 PMA 問題的兩個主要方法是驗證邏輯位置座標或大小範圍中，並驗證 UI 具有正確的 DPI。
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML 工具
Snoop，像是在 Visual Studio 中的 XAML 工具可協助診斷 PMA 問題。 一旦找到可能的問題，您可以設定中斷點，以及使用 [即時視覺化樹狀] 視窗，以及您在 [偵錯] 視窗中，檢查 UI 繫結和目前的 DPI。

## <a name="strategies-for-fixing-pma-issues"></a>修正 PMA 問題的策略

### <a name="replacing-dpihelper-calls"></a>取代 DpiHelper 呼叫
在大部分情況下，修正 UI 問題中 PMA 全然取代舊的 managed 程式碼中呼叫：*Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*並*Microsoft.VisualStudio.PlatformUI.DpiHelper*類別，呼叫新*Microsoft.VisualStudio.Utilities.DpiAwareness*協助程式類別。 

原生程式碼，它將需要取代呼叫舊*VsUI::CDpiHelper*類別的新呼叫*VsUI::CDpiAwareness*類別。 新的 DpiAwareness 和 CDpiAwareness 類別提供相同的轉換協助程式，因為 DpiHelper 類別，但需要額外的輸入的參數： 要做為參考用於轉換作業的 UI 元素。 

Managed 的 DpiAwareness 類別會提供 WPF 視覺效果、 Windows Form 控制項和 Win32 Hwnd 和 HMONITORs （兩者皆 IntPtrs 的形式），協助程式時的原生 CDpiAwareness 類別提供 HWND 及 HMONITOR helper。

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Form 對話方塊、 windows 或錯誤 DpiAwarenessContext 中顯示的控制項
即使不同 DpiAwarenessContext （因為 windows 預設行為） 與 windows 成功親子照顧，使用者仍然可能會看到不同 DpiAwarenessContext windows 以不同方式調整縮放問題。 如此一來，使用者可能會看到文字對齊/模糊不清或映像問題在 UI 上。

解決方法是設定應用程式中的所有視窗和控制項的正確 DpiAwarenessContext 範圍。

### <a name="tlmm-dialogs"></a>TLMM 對話方塊
在建立最上層的視窗，例如強制回應對話方塊時，務必確定在執行緒處於正確的狀態之前所建立的 HWND。 執行緒可以放入系統感知，藉由使用 CDpiScope helper 以原生或 DpiAwareness.EnterDpiScope 協助程式管理。 （在非 WPF 對話方塊/windows 上應通常到 TLMM）。

### <a name="child-level-mixed-mode-clmm"></a>子層級混合的模式 (CLMM)

根據預設，子視窗會收到相同的 DPI 感知模式，為其父系。 不過，您可以使用 SetThreadDpiHostingBehavior 覆寫它，而且有執行不同的縮放模式，比其父項或主機的子視窗。


#### <a name="clmm-issues"></a>CLMM 問題
在正確的 DPI 內容，應已在執行大部分的 UI 計算工作，會做為主要訊息迴圈或事件鏈結的一部分。 不過，如果座標或大小計算已完成這些主要工作流程外部 （例如期間是閒置時間的工作，或在 UI 執行緒中，目前的 DPI 內容可能不正確，導致 UI 錯置或正確調整大小的問題。 將執行緒放入正確的狀態中，ui 工作通常可以修正問題。
 
#### <a name="opting-out-of-clmm"></a>退出 CLMM
如果正在 PMA 的完整支援移轉非 WPF 工具視窗，它必須 CLMM 選擇退出。 若要這樣做，新的介面需要實作：IVsDpiAware。

C#: 
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++：
```cplusplus
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```
 

提供 managed 語言，來實作此介面的最佳位置是在相同的類別衍生自*Microsoft.VisualStudio.Shell.ToolWindowPane*。 針對C++，實作此介面的最佳位置是在相同的類別可實作*IVsWindowPane* vsshell.h 從。

介面上的 [模式] 屬性所傳回的值是 __VSDPIMODE （及轉型為 uint，以在受管理）：

```cs
enum __VSDPIMODE
    {
        VSDM_Unaware    = 0x01,
        VSDM_System     = 0x02,
        VSDM_PerMonitor = 0x03,
    }
```

- [工具] 視窗需要處理 96 DPI 感知的方式，Windows 會處理其調整為所有其他的 Dpi。 產生的有點模糊不清的內容。
- 系統意味著您需要處理的 DPI 的主要工具視窗會顯示 DPI。 比對的 DPI 的任何顯示看起來清晰，但如果 DPI 不同，或變更工作階段期間，Windows 將處理的縮放比例和它將會稍微變得模糊。
- PerMonitor 表示工具視窗必須處理在所有顯示器上的所有 Dpi，而且每當 DPI 變更時。

**注意**：Visual Studio 僅支援 PerMonitorV2 感知，因此 PerMonitor 列舉值會轉譯為 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 的 Windows 值。

## <a name="known-issues"></a>已知問題

### <a name="windows-forms"></a>Windows Forms

若要最佳化的新混合式案例中，Windows Forms 會變更目睹它建立控制項和視窗時未明確設定其父代。 更早版本，不使用明確的父控制項做為內部 「 暫止視窗 」 暫存的父控制項或正在建立的視窗。 

「 暫止期間 」 取得其 DpiAwarenessContext 從應用程式執行的處理序。 此控制項繼承相同的 DpiAwarenessContext 為暫止的視窗，並會接著會重設父代原始/預期的父系應用程式開發人員。  當控制項預期的父系不為所建立的控制項相同的 DpiAwarenessContext 將沒有作用。

截至.NET 4.8，如果父代未明確設定上的控制項或視窗中，Windows Form 會符合要求的控制項或視窗建立時的執行緒 DpiAwarenessContext 停車視窗查詢，並使用，為暫存的父代。 換句話說，在建立控制項現在已建立具有預期 DpiAwarenessContext。 視窗的控制項將然後會重設父代至預期的父代應用程式開發人員。
