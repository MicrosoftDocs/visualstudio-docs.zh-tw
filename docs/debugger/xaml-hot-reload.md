---
title: 撰寫和偵錯使用 XAML 熱重新載入的 XAML
description: 重新載入 XAML 經常性存取，或 XAML 編輯後繼續，可讓您對您的 XAML 程式碼中的變更，同時執行應用程式
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
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929137"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>撰寫和偵錯執行使用 Visual Studio 中的 XAML 熱重新載入的 XAML 程式碼

熱門的 visual Studio XAML 重新載入您建置 WPF 或 UWP 應用程式 UI，可讓您對 XAML 程式碼進行變更，您的應用程式執行時的協助。 這項功能可讓您以累加方式建置及測試與執行的應用程式資料內容、 驗證狀態和其他實際複雜度，很難在設計階段模擬的好處的 XAML 程式碼。

XAML 最忙碌的重新載入會在這些情況下特別有用：

* 修正偵錯模式中啟動應用程式之後，您的 XAML 程式碼中找到的 UI 問題。

* 建置應用程式的新 UI 元件已開發，同時利用您的應用程式執行階段內容。

|支援的應用程式類型|作業系統與工具|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 和更新版本 |
|通用 Windows app (UWP)|Windows 10 及更新版本，具有 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Visual Studio XAML 熱重新載入目前在 Visual Studio 中執行您的應用程式，附加偵錯工具時，才支援 (**F5**或是**開始偵錯**)。 您無法使用，以啟用這項體驗*附加至處理序*。

## <a name="known-limitations"></a>已知限制

以下是已知的 XAML 限制熱重新載入。 若要解決您遇到任何限制，只是停止偵錯工具，然後完成作業。

|限制|WPF|UWP|注意|
|-|-|-|-|
|將事件傳送至應用程式執行時的控制項|不支援|不支援|請參閱錯誤：*請確定事件失敗*|
|例如您的應用程式頁面] / [視窗中的資源字典中建立資源的物件或*App.xaml*|不支援|支援|範例： 新增```SolidColorBrush```做為資源字典```StaticResource```。</br>注意:靜態資源，樣式轉換器和其他項目寫入至的資源字典可以套用/使用同時使用 XAML 熱重新載入。 不支援資源的建立。</br> 變更資源字典```Source```屬性。| 
|將新控制項、 類別、 windows 或其他檔案新增至您的專案，應用程式執行時|不支援|不支援|None|
|管理 NuGet 套件 （新增/移除/更新套件）|不支援|不支援|None|
|變更資料繫結，會使用 {x： 繫結} 標記延伸|N/A|在 Visual Studio 2019 和更新版本支援|Visual Studio 2018 或先前版本中不支援|

## <a name="error-messages"></a>錯誤訊息

使用 XAML 熱重新載入時，您可能會遇到下列錯誤。

|錯誤訊息|描述|
|-|-|-|
|請確定事件失敗|錯誤指出您嘗試將事件傳送至其中一個您應用程式執行時不支援的控制項。|
|XAML 編輯後繼續找不到任何要更新的元素。|錯誤發生於您正在編輯熱重新載入的 XAML 無法更新您的應用程式中。</br> 此錯誤有時可藉由使用您執行的應用程式來瀏覽至 檢視使用 XAML 的位置。</br> 某些情況下，此錯誤表示在重新啟動偵錯工作階段之前，無法套用特定變更。 |
|偵錯工作階段期間不支援此變更。|錯誤表示 XAML 熱重新載入不支援您嘗試變更。 停止偵錯工作階段，進行變更，，然後重新啟動偵錯工作階段。|