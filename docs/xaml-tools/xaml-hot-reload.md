---
title: 使用 XAML 熱重新載入來撰寫和偵測 XAML
description: XAML 熱重新載入或 XAML [編輯後繼續] 可讓您在執行應用程式時變更 XAML 程式碼
ms.date: 09/23/2020
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11257561deecdbce4606207c3d59012a6d7c3d09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880316"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>使用 XAML 熱重新載入在 Visual Studio 中撰寫和偵測執行中的 XAML 程式碼

XAML 熱重新載入可讓您在應用程式執行時變更 XAML 程式碼，以協助您建立 WPF 或 UWP 應用程式使用者介面 (UI) 。 Visual Studio 和 Blend for Visual Studio 都有提供熱重新載入。 這項功能可讓您以累加的方式建立及測試 XAML 程式碼，並利用執行中應用程式資料內容的優點、驗證狀態，以及在設計階段時難以模擬的其他真實世界複雜度。 如果您需要針對 XAML 熱重新載入進行疑難排解的協助，請改為參閱 [疑難排解 XAML 熱重新載入](xaml-hot-reload-troubleshooting.md) 。

> [!NOTE]
> 如果您使用的是 Xamarin，請參閱 [適用于 xamarin 的 XAML 熱重新載入](/xamarin/xamarin-forms/xaml/hot-reload)。

在這些案例中，XAML 熱重新載入特別有用：

* 修正在偵測模式中啟動應用程式之後，在 XAML 程式碼中找到的 UI 問題。

* 針對正在開發的應用程式建立新的 UI 元件，同時利用應用程式的執行時間內容。

|支援的應用程式類型|作業系統與工具|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + 和 .NET Core</br>Windows 7 和更新版本 |
| (UWP) 的通用 Windows 應用程式|Windows 10 和更新版本，使用 [WINDOWS 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

下圖顯示如何使用「即時視覺化樹狀結構」來開啟您的原始程式碼，然後 XAML 熱重新載入變更按鈕文字和按鈕色彩。

![XAML 熱重新載入](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> 目前只有當您在 Visual Studio 中執行您的應用程式，或 Blend for Visual Studio 附加偵錯工具 (**F5** 或 **啟動調試** 程式) 時，才支援 Visual Studio XAML 熱重新載入。 除非您[手動設定環境變數](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)，否則您無法使用 [[附加至進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)] 來啟用此體驗。

## <a name="known-limitations"></a>已知的限制

以下是 XAML 熱重新載入的已知限制。 若要解決您遇到的任何限制，只要停止偵錯工具，然後完成操作即可。

|限制|WPF|UWP|備註|
|-|-|-|-|
|當應用程式正在執行時，將事件連接至控制項|不支援|不支援|請參閱錯誤： *確定事件失敗*。 請注意，在 WPF 中，您可以參考現有的事件處理常式。 在 UWP 應用程式中，不支援參考現有的事件處理常式。|
|在資源字典中建立資源物件，例如您應用程式的頁面/視窗或 *應用程式* 中的資源物件。|從 Visual Studio 2019 Update 2 開始支援|支援|範例：將加入 `SolidColorBrush` 至資源字典以做為使用 `StaticResource` 。</br>注意：使用 XAML 熱重新載入時，可以套用/使用靜態資源、樣式轉換器和其他寫入資源字典的元素。 不支援建立資源。</br> 變更資源字典 `Source` 屬性。|
|當應用程式正在執行時，將新的控制項、類別、視窗或其他檔案新增至專案|不支援|不支援|無|
|管理 NuGet 套件 (新增/移除/更新套件) |不支援|不支援|無|
|變更使用 {x:Bind} 標記延伸的資料系結|N/A|從 Visual Studio 2019 開始支援|這需要 Windows 10 1809 版 (組建 10.0.17763) 。 Visual Studio 2017 或之前版本中不支援。|
|不支援變更 X：Uid 指示詞|不適用|不支援|無|
|多個進程 | 支援 | 支援 | 在 Visual Studio 2019 [16.6 版](/visualstudio/releases/2019/release-notes-v16.6) 和更新版本中支援 |

## <a name="error-messages"></a>錯誤訊息

使用 XAML 熱重新載入時，您可能會遇到下列錯誤。

|錯誤訊息|Description|
|-|-|
|確定事件失敗|錯誤表示您嘗試將事件連接到您的其中一個控制項，而您的應用程式在執行時並不支援。|
|XAML 熱重新載入不支援這項變更，而且將不會在偵錯工具期間套用。|錯誤指出 XAML 熱重新載入不支援您嘗試的變更。 停止調試會話，進行變更，然後重新開機調試會話。 如果您發現不受支援的案例，請在 [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)中使用新的 [建議功能] 選項。 |

## <a name="see-also"></a>另請參閱

* [對 XAML 熱重新載入進行疑難排解](xaml-hot-reload-troubleshooting.md)
* [適用於 Xamarin.Forms 的 XAML 熱重新載入](/xamarin/xamarin-forms/xaml/hot-reload)
* [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
