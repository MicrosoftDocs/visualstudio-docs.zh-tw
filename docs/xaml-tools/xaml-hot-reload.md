---
title: 使用 XAML 熱重載來撰寫和調試 XAML
description: 「XAML 熱重載」或「XAML 編輯後繼續」可讓您在執行應用程式時變更 XAML 程式碼
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec1ca7ba801f4e3e0a7777e0cae62e78412dae6
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331962"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>在 Visual Studio 中使用 XAML 熱重載來撰寫和偵測執行中的 XAML 程式碼

XAML 熱重載可讓您在應用程式執行時變更 XAML 程式碼，以協助您建立 WPF 或 UWP 應用程式使用者介面（UI）。 「熱重載」可同時在 Visual Studio 和 Blend for Visual Studio 中使用。 這項功能可讓您以累加方式建立和測試 XAML 程式碼，並享有執行中應用程式的資料內容、驗證狀態，以及在設計階段中難以模擬的其他真實世界複雜度的優勢。 如果您需要針對 XAML 經常性載入進行疑難排解的說明，請參閱針對[Xaml 熱重載進行疑難排解](xaml-hot-reload-troubleshooting.md)。

> [!NOTE]
> 如果您使用的是 Xamarin，請參閱[適用于 xamarin 的 XAML 熱重載](/xamarin/xamarin-forms/xaml/hot-reload)。

在這些情況下，XAML 熱重載特別有用：

* 在應用程式以「偵測模式」啟動之後，修正在 XAML 程式碼中找到的 UI 問題。

* 為正在開發的應用程式建立新的 UI 元件，同時利用應用程式的執行時間內容。

|支援的應用程式類型|作業系統與工具|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + 和 .NET Core</br>Windows 7 和更新版本 |
|通用 Windows 應用程式（UWP）|Windows 10 和更新版本，含 [windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

下圖顯示如何使用 [即時視覺化樹狀] 來開啟您的原始程式碼，然後按 [XAML 熱重載] 來變更按鈕文字和按鈕色彩。

![XAML 熱重新載入](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> 目前只有當您在已附加偵錯工具的 Visual Studio 或 Blend for Visual Studio 中執行應用程式時，才支援 Visual Studio XAML 熱重載（**F5**或**開始進行調試**程式）。 除非您[手動設定環境變數](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)，否則無法使用 [[附加至進程] 來](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)啟用此體驗。

## <a name="known-limitations"></a>已知限制

以下是 XAML 熱重載的已知限制。 若要解決您遇到的任何限制，只要停止偵錯工具，然後完成作業即可。

|限制|WPF|UWP|注意|
|-|-|-|-|
|在應用程式執行時將事件接線至控制項|不支援|不支援|請參閱錯誤：*確認事件失敗*。 請注意，在 WPF 中，您可以參考現有的事件處理常式。 在 UWP 應用程式中，不支援參考現有的事件處理常式。|
|在資源字典中建立資源物件，例如在應用程式的頁面/視窗或*應用程式中。 xaml*|從 Visual Studio 2019 Update 2 開始支援|支援|範例：將加入 `SolidColorBrush` 至資源字典以當做使用 `StaticResource` 。</br>注意：使用 XAML 熱重載時，可以套用/使用靜態資源、樣式轉換器，以及寫入至資源字典的其他元素。 不支援建立資源。</br> 變更資源字典 `Source` 屬性。|
|當應用程式正在執行時，將新的控制項、類別、視窗或其他檔案加入至您的專案|不支援|不支援|無|
|管理 NuGet 套件（新增/移除/更新套件）|不支援|不支援|無|
|變更使用 {x:Bind} 標記延伸的資料系結|N/A|從 Visual Studio 2019 開始支援|這需要 Windows 10 版本1809（組建10.0.17763）。 Visual Studio 2017 或先前版本中不支援。|
|不支援變更 X：Uid 指示詞|不適用|不支援|無|
|多個進程 | 不支援 | 不支援 | 熱重載一次只能用於1個進程。 |

## <a name="error-messages"></a>錯誤訊息

使用 XAML 熱重載時，您可能會遇到下列錯誤。

|錯誤訊息|說明|
|-|-|
|確定事件失敗|錯誤表示您嘗試將事件連接到您的其中一個控制項，而您的應用程式在執行時並不支援。|
|XAML 熱重載不支援這項變更，而且將不會在進行偵錯工具期間套用。|錯誤表示 XAML 熱重載不支援您嘗試的變更。 停止「調試」會話、進行變更，然後重新開機「調試」會話。 如果您發現不支援的案例，請使用[Visual Studio 開發人員社區](https://developercommunity.visualstudio.com/spaces/8/index.html)中新的「建議功能」選項。 |

## <a name="see-also"></a>另請參閱

* [對 XAML 熱重新載入進行疑難排解](xaml-hot-reload-troubleshooting.md)
* [適用於 Xamarin.Forms 的 XAML 熱重新載入](/xamarin/xamarin-forms/xaml/hot-reload)
* [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
