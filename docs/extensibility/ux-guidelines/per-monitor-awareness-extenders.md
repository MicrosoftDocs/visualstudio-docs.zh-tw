---
title: Visual Studio 的擴充項的個別監視器感知支援
titleSuffix: ''
description: 深入了解新的擴充性支援，針對每個監視-感知用於 Visual Studio 2019。
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 44938c5753491521702867398a514f770cf831fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793631"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio 的擴充項的個別監視器感知支援
在 Visual Studio 2019 之前的版本有 DPI 感知上下文會設定為系統感知，而非個別監視器 DPI 感知 (PMA)。 執行中系統感知導致降低整體的視覺效果體驗 （例如模糊的字型或圖示），每當必須呈現之間不同的縮放比例或遠端機器使用不同的顯示設定例如 （不同的 Visual StudioWindows 調整)。

Visual Studio 2019 的 DPI 感知內容設為 PMA，環境支援此功能，讓 Visual Studio 來呈現根據其裝載所在的顯示設定，而不是單一系統定義的組態。 最終轉譯的 UI 一律務求支援 PMA 模式的介面區。

請參閱[高 DPI 桌面應用程式在 Windows 上開發](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)本文件涵蓋的條款及整體案例的詳細資訊的文件。

## <a name="quickstart"></a>快速入門
- 請確定 Visual Studio 正在執行中 PMA 模式 (請參閱**啟用 PMA**)

- 正確驗證您的擴充功能運作方式，跨一組常見的案例 (請參閱**測試您的擴充功能的 PMA 問題**)

- 如果您發現問題時，您可以使用這份文件所述的策略/建議來診斷和修正這些問題。 您也需要加入新[Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 封裝加入專案，以存取所需的 Api。

## <a name="enabling-pma"></a>啟用 PMA
若要啟用 Visual Studio 中的 PMA，必須符合下列需求：
1) Windows 10 April 2018 Update (v1803 RS4) 或更新版本
2) .NET framework 4.8 RTM 或更新版本
3) 使用 visual Studio 2019 [「 適用於具有不同像素密度的螢幕最佳化轉譯"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019)啟用選項

一旦符合這些需求時，Visual Studio 會自動跨處理序啟用 PMA 模式。

> [!NOTE]
> 只有在您有 Visual Studio 2019 Update #1 時，VS （例如屬性瀏覽器） 中的 Windows Form 內容將支援 PMA。

## <a name="testing-your-extensions-for-pma-issues"></a>測試您的擴充功能的 PMA 問題

Visual Studio 正式支援 WPF、 Windows Form、 microsoft、excel、win32 及 HTML/JS UI 架構。 當 Visual Studio 會置於 PMA 模式而定時，每個 UI 堆疊行為以不同的方式。 因此，不論 UI 架構，建議執行測試時，是為了要確保所有 UI 都會遵守 PMA 模式。

我們建議您驗證下列常見案例：

1. 在應用程式時執行 * 變更單一監視器環境的縮放比例
    - 此案例可協助測試到 UI 動態的 Windows DPI 變更回應

2. 停駐/卸除膝上型電腦，附加的監視設定為主要和附加的監視應用程式執行時，具有比膝上型電腦不同的縮放比例。
    - 此案例可協助測試 UI 會回應至顯示 DPI 變更，以及以動態方式處理顯示要加入或移除

3. 擁有多個具有不同的縮放比例的監視器，而且它們之間移動應用程式。
    - 此案例可協助測試顯示 DPI 變更，正在回應 UI
    
4. 遠端處理到機器當本機和遠端電腦的主要監視器有不同的縮放比例。
    - 此案例可協助測試到 UI 動態的 Windows DPI 變更回應

不論您的 UI 可能會發生問題的良好初步測試是程式碼會使用的是否*Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*， *Microsoft.VisualStudio.PlatformUI.DpiHelper*，或*VsUI::CDpiHelper*類別。 這些舊的 DpiHelper 類別僅支援系統 DPI 感知，而且不一定正確運作 PMA 程序時。

這些 DpiHelpers 的典型用法看起來像：

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

在上述範例中，表示視窗的邏輯界限的矩形會轉換成裝置單位，以便將它傳遞至原生方法 MonitorFromPoint 預期裝置座標，以傳回精確的監視器指標。

### <a name="classes-of-issues"></a>類別的問題
適用於 Visual Studio 啟用 PMA 模式時，UI 中數個常見的方式，導致複寫問題。 最，如果不是全部，這些問題，可能會發生在任何 Visual Studio 支援的 UI 架構。 此外，這些問題也可能發生時的 UI 裝載混合式 DPI 縮放比例的案例中 (請參閱 Windows[文件](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)若要了解更多)。 

#### <a name="win32-window-creation"></a>建立 Win32 視窗
使用建立時 windows CreateWindow() 或 CreateWindowEx()，常見的模式是建立在座標 (0，0) 的視窗 （主顯示器的左上角），然後將它移至其最終位置。 不過，這麼做可以讓視窗觸發程序的 DPI 變更訊息或事件，它可以重新觸發其他 UI 訊息或事件，並最終會導致不想要的行為或轉譯。

#### <a name="wpf-element-placement"></a>WPF 項目位置
當您移動使用舊的 Microsoft.VisualStudio.Utilities.Dpi.DpiHelper 的 WPF 項目，左上角座標可能不正確地計算時已非主要 DPI 的項目。

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>序列化的 UI 項目大小或位置
UI 大小或位置 （如果有另存為裝置單位） 會比它儲存在不同 DPI 內容還原時，它會定位和調整大小不正確。 這是因為裝置單位有固有的 DPI 關聯性。

#### <a name="incorrect-scaling"></a>不正確的縮放比例
但當移動至不同 DPI 的顯示器時，它們不重新調整，因此，最後是太大或太小，其內容時，會正確，調整主要 DPI 上建立的 UI 項目。

#### <a name="incorrect-bounding"></a>不正確的週框
同樣地，若要調整的問題，UI 項目會計算正確地在其主要的 DPI 內容，其界限但移至非主要 DPI 時，它們不會正確計算新的界限。 因此，內容的視窗最後會太小或太大，相較於主機的 UI 中，導致空白空間或裁剪。

#### <a name="drag--drop"></a>拖放
每當在混合式 DPI 案例 （例如不同 UI 項目呈現在不同 DPI 感知的模式）、 拖放座標可能是便常常，最終的置放位置結束設定不正確所導致。

#### <a name="out-of-process-ui"></a>跨處理序 UI
某些 UI 建立跨處理序，並建立外部程序是否在不同 DPI 感知的模式比 Visual Studio 中，這會導致任何先前的轉譯問題。

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Form 控制項、 影像或不正確地呈現的版面配置
並非所有的 Windows Form 內容支援 PMA 模式。 如此一來，您可能會看到轉譯不正確的版面配置問題，或調整。 可能的解決方案是在此情況下明確地呈現在 「 系統感知 」 DpiAwarenessContext 的 Windows Form 內容 (請參閱[強制控制項到特定的 DpiAwarenessContext](#forcing-a-control-into-a-specific-dpiawarenesscontext))。

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Form 控制項或視窗未顯示
此問題的主要原因之一是嘗試重設父代的控制項或視窗與視窗的一個 DpiAwarenessContext 不同 DpiAwarenessContext 與開發人員。

下圖顯示目前**預設**在 windows 的父代的 Windows 作業系統限制：

![正確的父代行為的螢幕擷取畫面](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> 您可以變更此行為，藉由設定執行緒裝載行為 (請參閱[DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior))。

如此一來，如果您將不受支援的模式之間的父子式關聯性時，它將會失敗，並控制或視窗可能不會如預期般轉譯。

### <a name="diagnosing-issues"></a>診斷問題
有許多因素需要考量識別 PMA 相關問題時： 

1. 執行 UI 或預期邏輯的 API 或裝置值。
    - WPF UI 和 Api 通常會使用邏輯值 （但不是一定）
    - Win32 UI 和 Api 通常會使用裝置的值

2. 值來自何處？
    - 如果從其他 UI 或 API 收到的值時，是它傳遞裝置或邏輯值。
    - 如果多個來源接收值，它們全都使用/期望相同類型的值還是轉換需要混搭嗎？

3. 使用中的 UI 常數和它們在何種形式是？

4. 是的執行緒中的值正確的 DPI 內容接收嗎？
    - 若要啟用混合式 DPI 裝載變更通常應該將程式碼路徑放在正確的內容，不過，外部的主要訊息迴圈或事件流程完成的工作可能會以錯誤的 DPI 內容中執行。

5. 值進行交叉 DPI 內容界限嗎？
    - 拖放在一般狀況的座標可以與 DPI 內容的位置。 視窗中嘗試執行正確的作業，但在某些情況下，主應用程式 UI 可能需要執行轉換工作，以確保相符的內容界限。

### <a name="pma-nuget-package"></a>PMA NuGet 套件
新的 DpiAwarness 程式庫可於[Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 套件。

### <a name="recommended-tools"></a>建議的工具
下列工具可協助您跨一些不同的 UI 堆疊支援 Visual Studio 偵錯 PMA 相關問題。

#### <a name="snoop"></a>窺探
Snoop 是 XAML 的偵錯工具具有內建的 Visual Studio XAML 工具不會有一些額外功能。 此外，Snoop 不需要主動偵錯 Visual Studio 能夠檢視和調整其 WPF UI。 Snoop 可用於診斷 PMA 問題的兩個主要方法是驗證邏輯位置座標或大小範圍中，並驗證 UI 具有正確的 DPI。
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML 工具
Snoop，像是在 Visual Studio 中的 XAML 工具可協助診斷 PMA 問題。 一旦找到可能的問題，您可以設定中斷點，以及使用 [即時視覺化樹狀] 視窗，以及您在 [偵錯] 視窗中，檢查 UI 繫結和目前的 DPI。

## <a name="strategies-for-fixing-pma-issues"></a>修正 PMA 問題的策略
### <a name="replacing-dpihelper-calls"></a>取代 DpiHelper 呼叫
在大部分情況下，修正 PMA 模式中的 UI 問題全然取代舊的 managed 程式碼中呼叫*Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*和*Microsoft.VisualStudio.PlatformUI.DpiHelper*類別，呼叫新*Microsoft.VisualStudio.Utilities.DpiAwareness*協助程式類別。 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

原生程式碼，它將需要取代呼叫舊*VsUI::CDpiHelper*類別的新呼叫*VsUI::CDpiAwareness*類別。 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

新的 DpiAwareness 和 CDpiAwareness 類別提供相同的單位轉換的協助程式 DpiHelper 類別，但需要額外的輸入的參數： 要做為參考用於轉換作業的 UI 元素。 務必要注意的映像調整 helper 還未存在於新的 DpiAwareness/CDpiAwareness 協助程式，並在必要時， [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019)應改為使用。

Managed 的 DpiAwareness 類別會提供 WPF 視覺效果、 Windows Form 控制項和 Win32 Hwnd 和 HMONITORs （兩者皆 IntPtrs 的形式），協助程式時的原生 CDpiAwareness 類別提供 HWND 及 HMONITOR helper。

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Form 對話方塊、 windows 或錯誤 DpiAwarenessContext 中顯示的控制項
即使不同 DpiAwarenessContexts （因為 Windows 預設行為） 與 windows 成功親子照顧，使用者仍然可能會看到使用自動調整規模問題做為視窗不同 DpiAwarenessContexts 調整規模以不同的方式。 如此一來，使用者可能會看到對齊/模糊的文字或影像在 UI 上的問題。

解決方法是設定應用程式中的所有視窗和控制項的正確 DpiAwarenessContext 範圍。

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>最上層的混合的模式 (TLMM) 對話方塊
在建立最上層的視窗，例如強制回應對話方塊時，務必確定會在之前的視窗 （和其控制代碼） 的正確狀態中所建立執行緒。 執行緒可以放入系統感知，藉由使用 CDpiScope helper 以原生或 DpiAwareness.EnterDpiScope 協助程式管理。 （在非 WPF 對話方塊/windows 上應通常到 TLMM）。

### <a name="child-level-mixed-mode-clmm"></a>子層級混合的模式 (CLMM)
依預設，子視窗接受目前的執行緒 DPI 感知內容如果建立不含父代或父項的 DPI 感知內容建立與父代時。 若要建立與其父系不同 DPI 感知內容子系，則可以將執行緒放到所需的 DPI 感知內容。 然後子系可以建立沒有父代，並手動重設父視窗父代。

#### <a name="clmm-issues"></a>CLMM 問題
在正確的 DPI 感知內容，應已在執行大部分的 UI 計算工作，會做為主要訊息迴圈或事件鏈結的一部分。 不過，如果座標或大小計算已完成這些主要工作流程外部 （例如期間是閒置時間的工作，或在 UI 執行緒中，目前的 DPI 感知內容可能不正確，導致 UI 錯置或正確調整大小的問題。 將執行緒放入正確的狀態中，ui 工作通常可以修正問題。
 
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

```cpp
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

> [!NOTE]
> Visual Studio 僅支援 PerMonitorV2 感知，因此 PerMonitor 列舉值會轉譯為 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 的 Windows 值。

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>強制控制項到特定的 DpiAwarenessContext
不會更新為支援 PMA 模式的舊版 UI 仍可能需要些微的修改時 Visual Studio 以 PMA 模式執行的工作。 一個這類修正牽涉到確定正在正確 DpiAwarenessContext 中建立 UI。 若要強制到特定的 DpiAwarenessContext 的 UI，您可以輸入 DPI 範圍為下列程式碼：

C#: 

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++：

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> 強制 DpiAwarenessContext 只適用於非 WPF UI 和最上層的 WPF 對話方塊。 建立 WPF UI，只是裝載於工具視窗或設計工具，只要內容會插入至 WPF UI 樹狀目錄中，當它取得轉換成目前的處理序 DpiAwarenessContext。

## <a name="known-issues"></a>已知問題
### <a name="windows-forms"></a>Windows Forms

若要最佳化的新混合式案例中，Windows Forms 會變更目睹它建立控制項和視窗時未明確設定其父代。 更早版本，不使用明確的父控制項做為內部 「 暫止視窗 」 暫存的父控制項或正在建立的視窗。 

.NET 4.8 之前沒有單一 「 暫止視窗 」，可從目前的執行緒 DPI 感知內容取得其 DpiAwarenessContext，在視窗的建立時間。 控制項的控制代碼建立，而且會被重設父代至最終/預期的父代的應用程式開發人員時，任何沒有父代的控制項就會繼承相同的 DpiAwarenessContext 為暫止的視窗。 如果 「 暫止期間 」 具有更高的 DpiAwarenessContext 比最終父視窗，這會導致執行時間為基礎的失敗。

截至.NET 4.8，目前沒有 「 暫止時間 」 的每個已發生的 DpiAwarenessContext。 另一個主要差異是，建立控制項時，不會建立控制代碼時，才將快取用於控制 DpiAwarenessContext。 這表示整體的結束行為相同，但可以將用來做為一致的問題以時間為基礎的問題。 它也提供應用程式開發人員更多具決定性的行為寫入其 UI 程式碼，並正確設定它的範圍。
