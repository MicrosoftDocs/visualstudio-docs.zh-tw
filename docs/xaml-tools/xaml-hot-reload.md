---
title: 使用 XAML 熱重新載入編寫與除錯 XAML
description: XAML 熱重新載入或 XAML 編輯並繼續,允許您在執行應用程式時更改 XAML 代碼
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880090"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>在視覺化工作室中使用 XAML 熱重新載入編寫和除錯執行 XAML 代碼

XAML 熱重裝允許您在應用運行時更改 XAML 代碼,從而説明您構建 WPF 或 UWP 應用使用者介面 (UI)。 熱重裝在視覺工作室和混合視覺工作室提供。 此功能使您能夠增量建構和測試 XAML 代碼,並受益於正在運行的應用的資料上下文、身份驗證狀態和其他在設計期間難以模擬的實際複雜性。 如果您需要説明排除 XAML 熱重新載入,請參閱[對 XAML 熱重新載入進行故障排除](xaml-hot-reload-troubleshooting.md)。

> [!NOTE]
> 如果使用 Xamarin.Forms,請參閱[XAML 熱重載入 Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)。

在以下情況下,XAML 熱重載入特別有用:

* 修復了在除錯模式下啟動應用後 XAML 代碼中發現的 UI 問題。

* 為正在開發的應用構建新的 UI 元件,同時利用應用的運行時上下文。

|支援的應用程式類型|作業系統與工具|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET 框架 4.6+ 和 .NET 核心</br>Windows 7 和更新版本 |
|通用 Windows 應用 (UWP)|Windows 10 及以上,具有 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393* |

下圖顯示了使用即時可視化樹打開原始碼,然後 XAML 熱重新載入以更改按鈕文本和按鈕顏色。

![XAML 熱重新載入](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML 熱重載入目前僅在在 Visual Studio 中運行應用程式或使用連接除錯器 **(F5**或**開始調試**)的可視化工作室混合時受支援。 除非[手動設置環境變數](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process),否則不能使用[Attach 來處理](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)啟用此體驗。

## <a name="known-limitations"></a>已知限制

以下是 XAML 熱重載入的已知限制。 要解決遇到的任何限制,只需停止調試器,然後完成該操作。

|限制|WPF|UWP|注意|
|-|-|-|-|
|在應用程式執行時將事件接線到控制項|不支援|不支援|請參考錯誤:*確保事件失敗*。 請注意,在 WPF 中,可以引用現有事件處理程式。 在 UWP 應用中,不支援引用現有事件處理程式。|
|在資源字典中建立資源物件,如應用程式的主頁/視窗或*App.xaml*中的資源物件|支援從視覺工作室 2019 更新 2|支援|範例:新增`SolidColorBrush`到資源字典中, 以便用作`StaticResource`。</br>注意:在使用 XAML 熱重新載入時,可以應用/使用寫入資源字典的靜態資源、樣式轉換器和其他元素。 僅不支援創建資源。</br> 更改資源字典`Source`屬性。|
|在應用程式執行時向專案新增新控制項、類別、視窗或其他檔案|不支援|不支援|None|
|管理 NuGet 套件 (新增/ 刪除/ 更新套件)|不支援|不支援|None|
|變更使用 {x:Bind} 標記延伸的資料繫結|N/A|支援從視覺工作室開始 2019|這需要 Windows 10 版本 1809(內部版本 10.0.17763)。 Visual Studio 2017 或早期版本中不支援。|
|不支援變更 x:Uid 指令|N/A|不支援|None|
|多個流程 | 不支援 | 不支援 | 熱重載一次只能針對 1 個進程。 |

## <a name="error-messages"></a>錯誤訊息

在使用 XAML 熱重新載入時,可能會遇到以下錯誤。

|錯誤訊息|描述|
|-|-|
|確保事件失敗|錯誤指示您嘗試將事件連接到其中一個控制項,而在應用程式運行時不支援該控制項。|
|XAML 熱重新載入不支援此更改,不會在調試會話期間應用。|錯誤表示 XAML 熱重新載入不支援您正在嘗試的更改。 停止調試會話,進行更改,然後重新啟動調試會話。 如果您發現一個不受支援的方案,您希望看到支援,請使用我們新的「建議功能」選項在[視覺化工作室開發人員社區](https://developercommunity.visualstudio.com/spaces/8/index.html)。 |

## <a name="see-also"></a>另請參閱

* [對 XAML 熱重新載入進行疑難排解](xaml-hot-reload-troubleshooting.md)
* [XAML 熱重載入 Xamarin.窗體](/xamarin/xamarin-forms/xaml/hot-reload)
* [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
