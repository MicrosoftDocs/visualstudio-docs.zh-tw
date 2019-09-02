---
title: 針對 Visual Studio 擴充項的個別監視器感知支援
titleSuffix: ''
description: 瞭解 Visual Studio 2019 中提供之個別監視器感知的新擴充項支援。
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585379"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>針對 Visual Studio 擴充項的個別監視器感知支援

Visual Studio 2019 之前的版本將其 DPI 感知內容設定為系統感知, 而不是針對個別監視器 DPI 感知 (PMA)。 在系統感知中執行時, 會導致視覺效果變差 (例如模糊字型或圖示), 只要 Visual Studio 必須在具有不同縮放比例的監視器之間轉譯, 或使用不同的顯示設定 (例如不同的) 在電腦上呈現Windows 調整)。

當環境支援 Visual Studio 2019 的 DPI 感知內容時, 會將其設定為 PMA, 讓 Visual Studio 根據其裝載位置 (而非單一系統定義的設定) 的顯示來呈現。 最後, 針對支援 PMA 模式的介面區, 將轉換成永遠清晰的 UI。

如需本檔中涵蓋之詞彙和整體案例的詳細資訊, 請參閱[Windows 上的高 DPI 桌面應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)檔。

## <a name="quickstart"></a>快速入門

- 確定 Visual Studio 在 PMA 模式中執行 (請參閱**啟用 PMA**)

- 驗證您的擴充功能可在一組常見案例中正常運作 (請參閱**測試擴充功能以 PMA 問題**)

- 如果您發現問題, 可以使用本檔中討論的策略/建議來診斷和修正這些問題。 您也需要將新的[VisualStudio DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 封裝新增至您的專案, 以存取所需的 api。

## <a name="enable-pma"></a>啟用 PMA

若要在 Visual Studio 中啟用 PMA, 必須符合下列需求:

- Windows 10 2018 年4月更新 (v1803、RS4) 或更新版本
- .NET Framework 4.8 RTM 或更新版本
- 已啟用 [[針對具有不同圖元密度的螢幕優化轉譯]](../../ide/reference/general-environment-options-dialog-box.md)選項 Visual Studio 2019

符合這些需求之後, Visual Studio 會自動在整個程式中啟用 PMA 模式。

> [!NOTE]
> 只有當您有 Visual Studio 2019 16.1 版或更新版本時, Visual Studio 中的 Windows Forms 內容 (例如, 屬性瀏覽器) 才支援 PMA。

## <a name="test-your-extensions-for-pma-issues"></a>測試擴充功能是否有 PMA 問題

Visual Studio 正式支援 WPF、Windows Forms、Win32 和 HTML/JS UI 架構。 當 Visual Studio 進入 PMA 模式時, 每個 UI 堆疊的行為會有所不同。 因此, 不論 UI 架構為何, 建議執行測試進行, 以確保所有 UI 都符合 PMA 模式。

建議您驗證下列常見案例:

- 在應用程式執行時變更單一監視環境的縮放比例。

  此案例可協助測試 UI 是否回應動態的 Windows DPI 變更。

- 在應用程式執行時, 將連接的監視設定為主要, 而附加的監視器與膝上型電腦的縮放比例不同, 以停駐/移除膝上型電腦。

  此案例可協助測試 UI 是否會回應顯示 DPI 的變更, 以及動態地新增或移除的處理顯示。

- 讓多個監視器具有不同的縮放比例, 並在其間移動應用程式。

  此案例可協助測試 UI 是否回應顯示 DPI 變更
    
- 當本機和遠端電腦的主要監視具有不同的縮放比例時, 遠端處理到電腦上。

  此案例可協助測試 UI 是否回應動態的 Windows DPI 變更。

無論您的 UI 是否使用*DpiHelper*、 *VisualStudio PlatformUI*或 DpiHelper *:: VsUI*類別, 都是很好的初步測試, 可以讓您瞭解是否有問題。 這些舊的 DpiHelper 類別僅支援系統 DPI 感知, 而且在 PMA 進程時, 不一定會正確運作。

這些 DpiHelpers 的一般用法如下所示:

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

在上述範例中, 代表視窗邏輯界限的矩形會轉換成裝置單位, 使其可以傳遞至預期裝置座標的原生方法 MonitorFromPoint, 以傳回精確的監視指標。

### <a name="classes-of-issues"></a>問題的類別
啟用 Visual Studio 的 PMA 模式時, UI 可能會以數種常見的方式來複寫問題。 大部分 (如果不是全部) 這些問題都可能發生在任何 Visual Studio 的支援 UI 架構中。 此外, 當 UI 在混合模式 DPI 縮放比例案例中裝載時, 也可能會發生這些問題 (請參閱 Windows[檔](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)以深入瞭解)。 

#### <a name="win32-window-creation"></a>建立 Win32 視窗
使用 CreateWindow () 或 CreateWindowEx () 建立 windows 時, 常見的模式是在座標 (0, 0) (主要顯示的左上角) 建立視窗, 然後將它移到其最終位置。 不過, 這麼做可能會導致視窗觸發 DPI 變更的訊息或事件, 這可能會重新觸發其他 UI 訊息或事件, 最後導致不想要的行為或轉譯。

#### <a name="wpf-element-placement"></a>WPF 元素位置
當使用舊的 DpiHelper 移動 WPF 專案時, 如果元素是非主要 DPI, 則左上角座標可能無法正確計算。

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI 元素大小或位置的序列化
當 UI 大小或位置 (如果另存為裝置單位) 還原到與儲存位置不同的 DPI 內容時, 它的位置和大小不正確。 發生這種情況的原因是裝置單位具有固有的 DPI 關聯性。

#### <a name="incorrect-scaling"></a>調整不正確
在主要 DPI 上建立的 UI 元素會正確調整, 不過, 當移動到具有不同 DPI 的顯示器時, 它們不會重新縮放, 而且其內容太大或太小。

#### <a name="incorrect-bounding"></a>不正確的界限
類似于縮放問題, UI 元素會在其主要 DPI 內容上正確地計算其界限, 不過, 當移動到非主要 DPI 時, 它們將不會正確地計算新界限。 因此, 相較于主控 UI, 內容視窗太小或太大, 因而導致空的空間或裁剪。

#### <a name="drag--drop"></a>拖曳 & drop
每當在混合模式 DPI 案例 (例如, 不同的 DPI 感知模式下呈現不同的 UI 專案) 內, 拖放座標可能會 miscalculated, 因此最終的放置位置最後會不正確。

#### <a name="out-of-process-ui"></a>跨進程 UI
有些 UI 是以跨進程的方式建立, 而且如果建立外部進程的 DPI 感知模式與 Visual Studio 不同, 這可能會引進任何先前的轉譯問題。

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>轉譯不正確的 Windows Forms 控制項、影像或版面配置
並非所有的 Windows Forms 內容都支援 PMA 模式。 因此, 您可能會看到呈現問題, 其中包含不正確的版面配置或縮放比例。 在此情況下, 可能的解決方法是明確地轉譯「系統感知」 DpiAwarenessCoNtext 中 Windows Forms 內容 (請參閱[強制控制項進入特定 DpiAwarenessCoNtext](#force-a-control-into-a-specific-dpiawarenesscontext))。

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms 控制項或 windows 未顯示
此問題的主要原因之一, 是開發人員嘗試將控制項或視窗以一個 DpiAwarenessCoNtext 重設為具有不同 DpiAwarenessCoNtext 的視窗。

下列影像顯示父視窗中目前的**預設**windows 作業系統限制:

![正確的父行為螢幕擷取畫面](media/PMA-parenting-behavior.PNG)

> [!Note]
> 您可以藉由設定執行緒裝載行為 (請參閱[Dpi_Hosting_Behavior 列舉](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)) 來變更此行為。

因此, 如果您在不支援的模式之間設定父子式關聯性, 它將會失敗, 而且控制項或視窗可能無法如預期般轉譯。

### <a name="diagnose-issues"></a>診斷問題

識別 PMA 相關的問題時, 有許多因素需要考慮: 

- UI 或 API 是否預期會有邏輯或裝置值？
    - WPF UI 和 Api 通常會使用邏輯值 (但不一定)
    - Win32 UI 和 Api 通常會使用裝置值

- 值來自何處？
    - 如果接收來自其他 UI 或 API 的值, 則會傳遞裝置或邏輯值。
    - 如果接收來自多個來源的值, 它們是否全部使用/預期相同類型的值, 或需要混合和比對轉換？

- 是否有使用中的 UI 常數和其形式？

- 在正確的 DPI 內容中, 執行緒是否會收到其所接收的值？

  啟用混合 DPI 裝載的變更通常應該將程式碼路徑放在正確的內容中, 不過, 在主要訊息迴圈以外完成的工作, 或事件流程可能會在錯誤的 DPI 內容中執行。

- 是否要跨 DPI 內容界限執行值？

  拖曳 & drop 是座標可以跨 DPI 內容進行的常見情況。 視窗會嘗試執行正確的動作, 但在某些情況下, 主機 UI 可能需要進行轉換工作, 以確保相符的內容界限。

### <a name="pma-nuget-package"></a>PMA NuGet 套件
新的 DpiAwarness 程式庫可以在[VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 套件中找到。

### <a name="recommended-tools"></a>建議的工具
下列工具可協助在 Visual Studio 支援的一些不同 UI 堆疊中, 對 PMA 相關的問題進行偵錯工具。

#### <a name="snoop"></a>窺探
[Snoop] 是 XAML 偵錯工具, 具有內建 Visual Studio XAML 工具沒有的一些額外功能。 此外, Snoop 不需要主動進行 debug Visual Studio, 就能夠查看和調整其 WPF UI。 在診斷 PMA 問題時, 兩個主要的方法是用來驗證邏輯位置座標或大小界限, 以及驗證 UI 是否有正確的 DPI。
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML 工具
如同 Snoop, Visual Studio 中的 XAML 工具可以協助診斷 PMA 問題。 一旦找到可能的原因, 您就可以設定中斷點, 並使用 [即時視覺化樹狀] 視窗和 [debug] 視窗來檢查 UI 界限和目前 DPI。

## <a name="strategies-for-fixing-pma-issues"></a>修正 PMA 問題的策略

### <a name="replace-dpihelper-calls"></a>取代 DpiHelper 呼叫

在大部分情況下, 修正 PMA 模式中的 UI 問題, 會將 managed 程式碼中的呼叫取代為舊的*DpiHelper 和 VisualStudio*類別, 並呼叫新*的VisualStudio 的 DpiAwareness* helper 類別。 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

針對機器碼, 它需要將對舊*VsUI:: CDpiHelper*類別的呼叫取代為新的*VsUI:: CDpiAwareness*類別的呼叫。 

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

新的 DpiAwareness 和 CDpiAwareness 類別提供與 DpiHelper 類別相同的單位轉換協助程式, 但需要額外的輸入參數: 用來做為轉換作業參考的 UI 元素。 請務必注意, 映射縮放協助程式不存在於新的 DpiAwareness/CDpiAwareness helper 中, 如有需要, 應改用[ImageService](../image-service-and-catalog.md) 。

Managed DpiAwareness 類別提供 WPF 視覺效果、Windows Forms 控制項和 Win32 Hwnd 和 HMONITORs 的協助程式 (兩者都以 IntPtrs 的形式), 而原生 CDpiAwareness 類別則提供 HWND 和 HMONITOR helper。

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>在錯誤的 DpiAwarenessCoNtext 中顯示 Windows Forms 對話方塊、視窗或控制項
即使在成功地將 windows 與不同的 DpiAwarenessCoNtexts (因為 Windows 預設行為) 結合之後, 使用者仍然可能會看到調整問題, 因為不同的 DpiAwarenessCoNtexts 縮放比例會有所不同。 因此, 使用者可能會在 UI 上看到對齊/模糊的文字或影像問題。

解決方案是為應用程式中的所有視窗和控制項設定正確的 DpiAwarenessCoNtext 範圍。

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>最上層混合模式 (TLMM) 對話方塊
建立最上層視窗 (例如強制回應對話方塊) 時, 請務必確定執行緒在建立視窗 (和其控制碼) 之前處於正確的狀態。 您可以使用原生中的 CDpiScope helper 或 managed 中的 DpiAwareness. EnterDpiScope helper, 將執行緒放入系統感知。 (TLMM 通常應該用於非 WPF 對話方塊/視窗。)

### <a name="child-level-mixed-mode-clmm"></a>子層級混合模式 (CLMM)
根據預設, 子視窗會在建立時不含父系, 或在使用父系建立父系的 DPI 感知內容時, 接收目前的執行緒 DPI 感知內容。 若要使用與父系不同的 DPI 感知內容來建立子系, 可以將執行緒放在所需的 DPI 感知內容中。 然後, 您可以在不使用父系的情況下建立子系, 並以手動方式重設父視窗的父級。

#### <a name="clmm-issues"></a>CLMM 問題
大部分在主要訊息迴圈或事件鏈中發生的 UI 計算工作, 應該已經在正確的 DPI 感知內容中執行。 不過, 如果座標或調整大小計算是在這些主要工作流程之外完成 (例如在閒置時間工作期間, 或關閉 UI 執行緒), 則目前的 DPI 感知內容可能會不正確, 而導致 UI misplacement 或錯誤調整大小的問題。 將執行緒放入 UI 工作的正確狀態, 通常會修正問題。
 
#### <a name="opt-out-of-clmm"></a>選擇不 CLMM
如果要將非 WPF 工具視窗遷移至完全支援 PMA, 則必須選擇不使用 CLMM。 若要這樣做, 必須執行新的介面:IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

對於 managed 語言而言, 執行此介面的最佳位置是在衍生自 VisualStudio 的相同類別中。 *ToolWindowPane*。 針對C++, 實作為此介面的最佳位置, 是在從 Vsshell 執行*IVsWindowPane*的相同類別中。

介面上的 Mode 屬性所傳回的值是 __VSDPIMODE (並轉換成 managed 中的 uint):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- [不知道] 表示工具視窗需要處理 96 DPI, Windows 將會處理所有其他 Dpi 的調整。 導致內容稍微模糊。
- [系統] 表示工具視窗需要處理主要顯示 DPI 的 DPI。 任何具有相符 DPI 的顯示畫面看起來都很簡潔, 但如果 DPI 不同或在會話期間變更, Windows 將會處理調整, 而且會稍微模糊。
- PerMonitor 表示工具視窗需要處理所有顯示器上的所有 Dpi, 以及每次 DPI 變更時。

> [!NOTE]
> Visual Studio 只支援 PerMonitorV2 感知, 因此 PerMonitor 列舉值會轉譯為 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 的 Windows 值。

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>強制控制項進入特定 DpiAwarenessCoNtext

未更新以支援 PMA 模式的舊版 UI, 在以 PMA 模式執行 Visual Studio 時, 仍可能需要進行次要調整以進行工作。 其中一種解決方法, 就是確定正在正確的 DpiAwarenessCoNtext 中建立 UI。 若要強制 UI 進入特定的 DpiAwarenessCoNtext, 您可以使用下列程式碼輸入 DPI 範圍:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> 強制 DpiAwarenessCoNtext 僅適用于非 WPF UI 和最上層 WPF 對話方塊。 建立要在工具視窗或設計工具中裝載的 WPF UI 時, 只要將內容插入 WPF UI 樹狀結構中, 它就會轉換成目前的進程 DpiAwarenessCoNtext。

## <a name="known-issues"></a>已知問題

### <a name="windows-forms"></a>Windows Forms

為了針對新的混合模式案例進行優化, Windows Forms 變更其父系未明確設定時, 如何建立控制項和視窗。 先前, 沒有明確父系的控制項使用內部「停車視窗」做為所建立之控制項或視窗的暫存父系。 

在 .NET 4.8 之前, 有一個「停車視窗」, 可從目前的執行緒 DPI 感知內容, 在視窗的建立時間取得其 DpiAwarenessCoNtext。 當控制項的控制碼建立時, 任何無上層控制項都會繼承與停車視窗相同的 DpiAwarenessCoNtext, 而應用程式開發人員會將其重設為最終/預期父系的父代。 如果「停車視窗」的 DpiAwarenessCoNtext 高於最終的父視窗, 這會導致以時間為基礎的失敗。

從 .NET 4.8 開始, 目前已遇到的每個 DpiAwarenessCoNtext 都有「停車視窗」。 另一個主要差異是建立控制項時, 會快取用於控制項的 DpiAwarenessCoNtext, 而不是在建立控制碼時快取。 這表示整體端行為相同, 但是可以將用來做為時間型問題的內容轉換成一致的問題。 它也會為應用程式開發人員提供更具決定性的行為, 以撰寫其 UI 程式碼並正確設定其範圍。
