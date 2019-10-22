---
title: 在自動程式化 UI 測試中使用 HTML5 控制項
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: e9118dc94019f40289730be78c28777fb86d89db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659772"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>在自動程式化 UI 測試中使用 HTML5 控制項

自動程式化 UI 測試支援 Internet Explorer 9 和 Internet Explorer 10 所含的一些 HTML5 控制項。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio 企業版

> [!WARNING]
> 在 Internet Explorer 10 之前的版本，可以在相較於 Internet Explorer 處理序更高的權限層級中，執行自動程式碼 UI 測試。 在 Internet Explorer 10 執行自動程式碼 UI 測試時，自動程式碼 UI 測試和 Internet Explorer 程序必須是相同的權限層級。 這是因為 Internet Explorer 10 中的 AppContainer 功能更安全。

> [!WARNING]
> 如果您在 Internet Explorer 10 中建立自動程式碼 UI 測試，可能無法使用 Internet Explorer 9 或 Internet Explorer 8 執行。 這是因為 Internet Explorer 10 包含 HTML5 控制項，例如 Audio、Video、ProgressBar 和 Slider。 Internet Explorer 9 或 Internet Explorer 8 無法辨識這些 HTML5 控制項。 同樣地，使用 Internet Explorer 9 的自動程式碼 UI 測試可能包含一些 Internet Explorer 8 無法辨識的 HTML5 控制項。

## <a name="audio-control"></a>音訊控制項

**音訊控制項：** 正確記錄和播放 HTML5 Audio 控制項上的動作。

![HTML5 Audio 控制項](../test/media/codedui_html5_audio.png)

|動作|錄製|產生的程式碼|
|-|---------------|-|
|**播放音訊**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|從 00:00:00 播放 \<名稱> 音訊|HtmlAudio.Play(TimeSpan)|
|**搜尋音訊的特定時間**|搜尋 \<名稱> 音訊的 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**暫停音訊**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|在 00:01:53 暫停 \<名稱> 音訊|HtmlAudio.Pause(TimeSpan)|
|**音訊靜音**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|將 \<名稱> 音訊靜音|HtmlAudio.Mute()|
|**音訊取消靜音**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|將 \<名稱> 音訊取消靜音|HtmlAudio.Unmute()|
|**變更音訊的音量**|將 \<名稱> 音訊的音量設為 79%|HtmlAudio.SetVolume(float)|

請參閱 [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement)，以取得您可以在其上新增判斷提示的屬性清單。

**搜尋屬性：** `HtmlAudio` 的搜尋屬性是 `Id`、`Name` 和 `Title`。

**篩選屬性：** `HtmlAudio` 的篩選屬性是 `Src`、`Class`、`ControlDefinition` 和 `TagInstance`。

> [!NOTE]
> 搜尋和暫停的時間量可以很大。 在播放時，自動程式碼 UI 測試會等到 `(TimeSpan)` 中指定的時間才暫停音訊。 如果因為某些特殊情況，已經過所指定的時間才按下 [暫停] 命令，就會擲回例外狀況。

## <a name="video-control"></a>視訊控制項
**視訊控制項：** 正確記錄和播放 HTML5 Video 控制項上的動作。

![HTML5 Video 控制項](../test/media/codedui_html5_video.png)

|動作|錄製|產生的程式碼|
|-|---------------|-|
|**播放視訊**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|從 00:00:00 播放 \<名稱> 視訊|HtmlVideo.Play(TimeSpan)|
|**搜尋視訊的特定時間**|搜尋 \<名稱> 視訊的 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**暫停視訊**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|在 00:01:53 暫停 \<名稱> 視訊|HtmlVideo.Pause(TimeSpan)|
|**視訊靜音**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|將 \<名稱> 視訊靜音|HtmlVideo.Mute()|
|**視訊取消靜音**<br /><br /> 直接從控制項，或是從控制項的右鍵功能表。|將 \<名稱> 視訊取消靜音|HtmlVideo.Unmute()|
|**變更視訊的音量**|將 \<名稱> 視訊的音量設為 79%||

請參閱 [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video)，以取得您可以在其上新增判斷提示的屬性清單。

**搜尋屬性：** `HtmlVideo` 的搜尋屬性是 `Id`、`Name` 和 `Title`。

**篩選屬性：** `HtmlVideo` 的篩選屬性是 `Src`、`Poster`、`Class`、`ControlDefinition` 和 `TagInstance`。

> [!NOTE]
> 如果您使用 -30s 或 +30s 標籤倒轉或向前快轉視訊時，會彙總以搜尋至適當的時間。

## <a name="progressbar"></a>進度列
**ProgressBar 控制項：** ProgressBar 是不可互動的控制項。 您可以在此控制項的 `Value` 和 `Max` 屬性上加入判斷提示。 如需詳細資訊，請參閱 [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress)。

![HTML5 ProgressBar 控制項](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>請參閱

- [HTML 項目](https://developer.mozilla.org/docs/Web/HTML/Element)
- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
