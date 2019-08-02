---
title: 使用 XAML 熱重載來撰寫和調試 XAML
description: 「XAML 熱重載」或「XAML 編輯後繼續」可讓您在執行應用程式時變更 XAML 程式碼
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1b2428024c30b8f96babf0cab6a56c60f52fa57
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711215"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>在 Visual Studio 中使用 XAML 熱重載來撰寫和偵測執行中的 XAML 程式碼

Visual Studio XAML 熱重載可協助您在應用程式執行時變更 XAML 程式碼, 藉此建立 WPF 或 UWP 應用程式 UI。 這項功能可讓您以累加方式建立和測試 XAML 程式碼, 並享有執行中應用程式的資料內容、驗證狀態, 以及在設計階段中難以模擬的其他真實世界複雜度的優勢。

在這些情況下, XAML 熱重載特別有用:

* 在應用程式以「偵測模式」啟動之後, 修正在 XAML 程式碼中找到的 UI 問題。

* 為正在開發的應用程式建立新的 UI 元件, 同時利用應用程式的執行時間內容。

|支援的應用程式類型|作業系統與工具|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 和更新版本 |
|通用 Windows 應用程式 (UWP)|Windows 10 和更新版本, 含 [windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> 目前只有當您在已附加偵錯工具的 Visual Studio 中執行應用程式時, 才支援 Visual Studio XAML 熱重載 (**F5**或**開始進行調試**程式)。 您無法使用 [*附加至進程*] 來啟用此體驗。

## <a name="known-limitations"></a>已知限制

以下是 XAML 熱重載的已知限制。 若要解決您遇到的任何限制, 只要停止偵錯工具, 然後完成作業即可。

|限制|WPF|UWP|附註|
|-|-|-|-|
|在應用程式執行時將事件接線至控制項|不支援|不支援|請參閱錯誤:*確定事件失敗*|
|在資源字典中建立資源物件, 例如在應用程式的頁面/視窗或*應用程式中。 xaml*|不支援|支援|範例: 將```SolidColorBrush```加入至資源字典以當做使用```StaticResource```。</br>注意:使用 XAML 熱重載時, 可以套用/使用靜態資源、樣式轉換器, 以及寫入至資源字典的其他元素。 不支援建立資源。</br> 變更資源字典```Source```屬性。| 
|當應用程式正在執行時, 將新的控制項、類別、視窗或其他檔案加入至您的專案|不支援|不支援|None|
|管理 NuGet 套件 (新增/移除/更新套件)|不支援|不支援|None|
|變更使用 {x:Bind} 標記延伸的資料系結|N/A|Visual Studio 2019 和更新版本中支援|Visual Studio 2017 或之前版本中不支援|

## <a name="error-messages"></a>錯誤訊息

使用 XAML 熱重載時, 您可能會遇到下列錯誤。

|錯誤訊息|描述|
|-|-|-|
|確定事件失敗|錯誤表示您嘗試將事件連接到您的其中一個控制項, 而您的應用程式在執行時並不支援。|
|XAML 編輯後繼續找不到任何要更新的元素。|當您編輯的 XAML 無法在您的應用程式中更新熱重載時, 就會發生錯誤。</br> 有時候, 您可以使用執行中的應用程式來流覽至使用 XAML 的視圖, 以修正此錯誤。</br> 有時候, 此錯誤表示在您重新開機偵錯工具會話之前, 無法套用特定的變更。 |
|偵錯工作階段期間不支援此變更。|錯誤表示 XAML 熱重載不支援您嘗試的變更。 停止「調試」會話、進行變更, 然後重新開機「調試」會話。|
