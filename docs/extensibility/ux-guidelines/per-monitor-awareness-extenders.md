---
title: Visual Studio 擴充項的 Per-Monitor 感知支援
titleSuffix: ''
description: 瞭解 Visual Studio 2019 中可用之個別監視器感知的新擴充項支援。
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902042"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio 擴充項的 Per-Monitor 感知支援

Visual Studio 2019 之前的版本，其 DPI 感知內容會設定為系統感知，而不是個別監視器 DPI 感知 (PMA) 。 在系統感知中執行，會導致視覺效果變差 (例如模糊字型或圖示) 每次 Visual Studio 必須在不同的縮放比例之間轉譯，或從遠端進入不同的顯示器設定 (例如，不同的 Windows 調整) 。

當環境支援時，Visual Studio 2019 的 DPI 感知內容會設定為 PMA，允許 Visual Studio 根據其裝載位置的設定進行轉譯，而不是以單一系統定義的設定呈現。 最終轉譯為支援 PMA 模式之介面區的永遠清晰 UI。

如需本檔中涵蓋的條款和整體案例的詳細資訊，請參閱 [Windows 檔上的高 DPI 桌面應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 檔。

## <a name="quickstart"></a>快速入門

- 確定 Visual Studio 正在 PMA 模式中執行 (請參閱 **啟用 PMA**) 

- 驗證您的延伸模組可在一組常見案例中正確運作 (查看 **PMA 問題的測試延伸** 模組) 

- 如果您發現問題，您可以使用本檔中討論的策略/建議來診斷和修正這些問題。 您也必須將新的 [VisualStudio DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 套件新增至您的專案，才能存取所需的 api。

## <a name="enable-pma"></a>啟用 PMA

若要在 Visual Studio 中啟用 PMA，必須符合下列需求：

- Windows 10 2018 年4月更新 (v1803、RS4) 或更新版本
- .NET Framework 4.8 RTM 或更新版本
- 已啟用「 [針對具有不同圖元密度的螢幕優化呈現](../../ide/reference/general-environment-options-dialog-box.md) 」選項的 Visual Studio 2019

符合這些需求之後，Visual Studio 會自動啟用整個進程的 PMA 模式。

> [!NOTE]
> Visual Studio 中的 Windows Forms 內容 (例如，屬性瀏覽器) 只有當您有 Visual Studio 2019 16.1 版或更新版本時才支援 PMA。

## <a name="test-your-extensions-for-pma-issues"></a>測試擴充功能的 PMA 問題

Visual Studio 正式支援 WPF、Windows Forms、Win32 和 HTML/JS UI 架構。 當 Visual Studio 進入 PMA 模式時，每個 UI 堆疊的行為會有所不同。 因此，無論何種 UI 架構，建議您執行測試，以確保所有 UI 都符合 PMA 模式。

建議您驗證下列常見案例：

- 當應用程式正在執行時，變更單一監視器環境的縮放比例。

  此案例可協助測試 UI 是否回應動態 Windows DPI 變更。

- 在應用程式執行時，將連結的監視設定為主要電腦，並將連接的監視與膝上型電腦具有不同的縮放比例，以停駐/移除膝上型電腦。

  此案例可協助測試 UI 是否回應顯示 DPI 變更，以及動態地新增或移除的顯示。

- 讓多個監視器具有不同的縮放比例，並在兩者之間移動應用程式。

  此案例可協助測試 UI 是否回應顯示 DPI 變更
    
- 當本機和遠端電腦的主要監視器具有不同的縮放比例時，會在電腦上進行遠端處理。

  此案例可協助測試 UI 是否回應動態 Windows DPI 變更。

若要瞭解您的 UI 是否有問題，有一個很好的初步測試，就是程式碼是否會使用 *DpiHelper*、 *VisualStudio. PlatformUI. DpiHelper* 或 *VsUI：： CDpiHelper* 類別。 這些舊的 DpiHelper 類別僅支援系統 DPI 感知，而且在 PMA 程式時，不一定會正確運作。

這些 DpiHelpers 的一般用法如下所示：

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

在上述範例中，代表視窗邏輯界限的矩形會轉換成裝置單位，讓它可以傳遞至預期裝置座標的原生方法 MonitorFromPoint，以便傳回正確的監視器指標。

### <a name="classes-of-issues"></a>問題類別
當 Visual Studio 啟用 PMA 模式時，UI 會以數種常見的方式複寫問題。 這些問題大多都可能發生在任何 Visual Studio 支援的 UI 架構中。 此外，當您在混合模式的 DPI 縮放案例中裝載 UI 時，也可能會發生這些問題 (請參閱 Windows [檔](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) ，以深入瞭解) 。 

#### <a name="win32-window-creation"></a>建立 Win32 視窗
建立具有 CreateWindow () 或 CreateWindowEx () 的 windows 時，常見的模式是在座標 (0、0)  (主顯示器) 的左上角，然後將其移至其最終位置。 不過，這麼做可能會導致視窗觸發 DPI 變更的訊息或事件，這可能會重新觸發其他 UI 訊息或事件，最後導致不想要的行為或轉譯。

#### <a name="wpf-element-placement"></a>WPF 元素放置
使用舊的 VisualStudio 來移動 WPF 專案時，如果專案是在非主要 DPI 上，則可能無法正確計算左上角座標。

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI 元素大小或位置的序列化
當 UI 大小或位置 (如果另存為裝置單位) 在不同于其儲存位置的 DPI 內容上還原時，它的位置和大小會不正確。 發生這種情況是因為裝置單位具有固有的 DPI 關聯性。

#### <a name="incorrect-scaling"></a>調整不正確
在主要 DPI 上建立的 UI 元素將會正確地調整，不過，當移至具有不同 DPI 的顯示器時，不會重新調整，而且其內容太大或太小。

#### <a name="incorrect-bounding"></a>不正確的周框
類似于調整問題，UI 專案會在其主要 DPI 內容上正確計算其界限，不過，當移至非主要 DPI 時，它們將不會正確地計算新的界限。 因此，相較于裝載 UI，內容視窗太小或太大，這會造成空白或裁剪。

#### <a name="drag--drop"></a>拖曳 & drop
每次在混合模式 DPI 案例中 (例如，在不同的 DPI 感知模式下轉譯不同的 UI 專案) 、拖放座標可能會 miscalculated，導致最終的放置位置最後出現錯誤。

#### <a name="out-of-process-ui"></a>跨進程 UI
有些 UI 是跨進程建立的，而且如果建立的外部進程與 Visual Studio 的 DPI 感知模式不同，這可能會導致任何先前的轉譯問題。

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>未正確轉譯 Windows Forms 控制項、影像或版面配置
並非所有的 Windows Forms 內容都支援 PMA 模式。 如此一來，您可能會看到轉譯或調整不正確的問題。 在此情況下，可能的解決方案是在「系統感知」 DpiAwarenessCoNtext 中明確轉譯 Windows Forms 內容 (請參閱 [強制控制項進入特定的 DpiAwarenessCoNtext](#force-a-control-into-a-specific-dpiawarenesscontext)) 。

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms 控制項或 windows 未顯示
此問題的主要原因之一，就是開發人員嘗試將具有一個 DpiAwarenessCoNtext 的控制項或視窗重設成具有不同 DpiAwarenessCoNtext 的視窗。

下列影像顯示在父視窗中目前 **預設** 的 Windows 作業系統限制：

![正確的父行為螢幕擷取畫面](media/PMA-parenting-behavior.PNG)

> [!Note]
> 您可以藉由設定執行緒裝載行為來變更此行為 (請參閱 [Dpi_Hosting_Behavior 列舉](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)) 。

如此一來，如果您設定不支援模式之間的父子式關聯性，它將會失敗，而且控制項或視窗可能無法如預期般轉譯。

### <a name="diagnose-issues"></a>診斷問題

在識別與 PMA 相關的問題時，有許多因素需要考慮： 

- UI 或 API 是否預期邏輯或裝置值？
    - WPF UI 和 Api 通常會使用邏輯值 (但不一定會) 
    - Win32 UI 和 Api 通常會使用裝置值

- 值來自何處？
    - 如果接收來自其他 UI 或 API 的值，則會傳遞裝置或邏輯值。
    - 如果接收來自多個來源的值，它們會使用/預期相同類型的值，還是需要混合和比對轉換？

- 使用中的 UI 常數以及其所在的表單為何？

- 執行緒是否在其所接收的值的正確 DPI 內容中？

  啟用混合 DPI 裝載的變更通常應該會將程式碼路徑放在正確的內容中，不過，在主要訊息迴圈以外完成的工作，或事件流程可能會在錯誤的 DPI 內容中執行。

- 是否要跨 DPI 內容界限進行值？

  拖曳 & drop 是座標可以跨 DPI 內容的常見情況。 視窗嘗試執行正確的動作，但在某些情況下，主機 UI 可能需要進行轉換工作，以確保符合內容界限。

### <a name="pma-nuget-package"></a>PMA NuGet 套件
您可以在 [VisualStudio DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 套件中找到新的 DpiAwarness 程式庫。

### <a name="recommended-tools"></a>建議工具
下列工具可協助您跨 Visual Studio 所支援的一些不同 UI 堆疊，來偵測 PMA 相關的問題。

#### <a name="snoop"></a>探聽
Snoop 是 XAML 偵錯工具，它有內建 Visual Studio XAML 工具沒有的額外功能。 此外，Snoop 不需要主動進行 Visual Studio 的 debug 錯，就能查看和調整其 WPF UI。 您可以利用這兩種主要方式來診斷 PMA 問題：驗證邏輯放置座標或大小界限，以及驗證 UI 是否有正確的 DPI。
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML 工具
就像 Snoop 一樣，Visual Studio 中的 XAML 工具可以協助診斷 PMA 問題。 一旦找到可能的原因之後，您就可以設定中斷點，並使用 [即時視覺化樹狀結構] 視窗和 [偵錯工具] 視窗，檢查 UI 界限和目前的 DPI。

## <a name="strategies-for-fixing-pma-issues"></a>修正 PMA 問題的策略

### <a name="replace-dpihelper-calls"></a>取代 DpiHelper 呼叫

在大部分的情況下，在 PMA 模式中修正 UI 問題，以將 managed 程式碼中的呼叫取代為 VisualStudio 類別，並呼叫新的 *DpiHelper* 和 VisualStudio. PlatformUI 類別，並呼叫新的和 *。* DpiHelper 協助 *程式* 類別。 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

若為機器碼，則需要使用新的 *VsUI：： CDpiAwareness* 類別的呼叫來取代舊 *VsUI：： CDpiHelper* 類別的呼叫。 

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

新的 DpiAwareness 和 CDpiAwareness 類別提供與 DpiHelper 類別相同的單位轉換協助程式，但需要額外的輸入參數：用來做為轉換作業參考的 UI 元素。 請務必注意，影像縮放協助程式不存在於新的 DpiAwareness/CDpiAwareness 協助程式中，如有需要，則應改用 [>imageservice](../image-service-and-catalog.md) 。

Managed DpiAwareness 類別提供 WPF 視覺效果、Windows Forms 控制項，以及 Win32 Hwnd 和 (HMONITORs 的協助程式，兩者都是 IntPtrs) 的格式，而原生 CDpiAwareness 類別則提供 HWND 和 HMONITOR 協助程式。

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms 的對話方塊、視窗或控制項顯示在錯誤的 DpiAwarenessCoNtext 中
即使在成功將 windows 的父代與不同 DpiAwarenessCoNtexts (的情況下，因為 Windows 預設行為) ，使用者仍可能看到調整問題，因為具有不同 DpiAwarenessCoNtexts 調整規模的視窗不同。 因此，使用者可能會在 UI 上看到對齊/模糊的文字或影像問題。

解決方案是為應用程式中的所有視窗和控制項設定正確的 DpiAwarenessCoNtext 範圍。

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>最上層混合模式 (TLMM) 對話方塊
建立最上層視窗（例如強制回應對話方塊）時，請務必確定執行緒在視窗 (之前處於正確的狀態，並) 建立其控制碼。 您可以使用原生中的 CDpiScope helper 或 managed 中的 DpiAwareness EnterDpiScope helper，將執行緒放入系統感知中。  (TLMM 一般應該用於非 WPF 對話方塊/視窗。 ) 

### <a name="child-level-mixed-mode-clmm"></a>子層級混合模式 (CLMM) 
根據預設，如果在建立時沒有父代，子視窗會收到目前的執行緒 DPI 感知內容，或父系的 DPI 感知內容。 若要使用與父系不同的 DPI 感知內容來建立子系，則可以將執行緒放入所需的 DPI 感知內容中。 然後，您可以建立不含父系的子系，並以手動方式重設父視窗的父級。

#### <a name="clmm-issues"></a>CLMM 問題
大部分作為主要訊息迴圈或事件鏈一部分的 UI 計算工作，都應該已在正確的 DPI 感知內容中執行。 但是，如果座標或調整大小計算是在這些主要工作流程之外進行 (例如在閒置時間工作或關閉 UI 執行緒時），則目前的 DPI 感知內容可能不正確，導致 UI misplacement 或錯誤調整大小的問題。 讓執行緒進入 UI 工作的正確狀態通常可修正問題。
 
#### <a name="opt-out-of-clmm"></a>退出 CLMM
如果非 WPF 工具視窗正在遷移，以完全支援 PMA，則必須選擇不使用 CLMM。 若要這樣做，必須實作為新介面： IVsDpiAware。

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

針對 managed 語言，執行這個介面的最佳位置是在衍生自 VisualStudio 的相同類別中。 *ToolWindowPane*。 針對 c + +，執行這個介面的最佳位置是在從 vsshell 執行 *IVsWindowPane* 的相同類別中。

介面上的 Mode 屬性所傳回的值是 __VSDPIMODE (，並在 managed) 中轉換成 uint：

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- 未察覺表示工具視窗需要處理 96 DPI，Windows 將會處理所有其他 Dpi 的縮放比例。 導致內容稍微模糊不清。
- 系統表示工具視窗需要處理主顯示器 DPI 的 DPI。 具有相符 DPI 的任何顯示器看起來都很清晰，但如果 DPI 在會話期間不同或有所變更，則 Windows 將會處理調整，而且會稍微模糊。
- PerMonitor 表示工具視窗必須處理所有顯示器上的所有 Dpi，以及每次 DPI 變更的時間。

> [!NOTE]
> Visual Studio 只支援 PerMonitorV2 感知，因此 PerMonitor 列舉值會轉譯為 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 的 Windows 值。

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>強制控制項進入特定的 DpiAwarenessCoNtext

未更新以支援 PMA 模式的舊版 UI，在 Visual Studio 以 PMA 模式執行時，可能仍需要進行輕微的調整才能運作。 其中一種解決方法，就是確定正在正確的 DpiAwarenessCoNtext 中建立 UI。 若要強制 UI 進入特定的 DpiAwarenessCoNtext，您可以使用下列程式碼輸入 DPI 範圍：

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
> 強制 DpiAwarenessCoNtext 僅適用于非 WPF UI 和最上層 WPF 對話方塊。 當您建立要在工具視窗或設計工具內裝載的 WPF UI 時，只要將內容插入 WPF UI 樹狀結構中，就會轉換成目前的進程 DpiAwarenessCoNtext。

## <a name="known-issues"></a>已知問題

### <a name="windows-forms"></a>Windows Forms

為了針對新的混合模式案例進行優化，Windows Forms 變更了控制項和視窗在未明確設定時的建立方式。 稍早，沒有明確父系的控制項使用內部「停車視窗」做為要建立之控制項或視窗的暫存父代。 

在 .NET 4.8 之前，有一個「停車視窗」，可在視窗的建立時間從目前的執行緒 DPI 感知內容取得其 DpiAwarenessCoNtext。 當控制項的控制碼建立時，任何無上層控制項都會繼承與停車視窗相同的 DpiAwarenessCoNtext，並且會將其重設為應用程式開發人員的最終/預期父系。 如果 "停車視窗" 的 DpiAwarenessCoNtext 高於最後一個父視窗，這會導致以時間為基礎的失敗。

從 .NET 4.8 開始，目前已遇到的每個 DpiAwarenessCoNtext 都有一個「停車視窗」。 另一個主要差異是，在建立控制項時，會快取用於控制項的 DpiAwarenessCoNtext，而不是在建立控制碼時快取。 這表示整體的結束行為是相同的，但可以將以時間為基礎的問題變成一致的問題。 它也可讓應用程式開發人員更具決定性的行為來撰寫 UI 程式碼，並正確地設定其範圍。
