---
title: 使用不同的 Web 瀏覽器搭配自動程式化 UI 測試
description: 瞭解如何自訂您的測試，並針對您的 web 應用程式使用不同的瀏覽器加以播放。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 199b8a3852850e1bb3239ad3b70ee5a438d4bcbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850044"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>使用不同的網頁瀏覽器搭配自動程式化 UI 測試

自動程式化 UI 測試可以使用 Internet Explorer 錄製測試，以自動測試 Web 應用程式。 之後，您可以自訂測試再使用 Internet Explorer 或其他瀏覽器類型的 Web 應用程式進行播放。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

首先，安裝自動 [程式碼 UI 跨瀏覽器測試的 Selenium 元件](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)。

## <a name="whats-supported-across-all-web-browsers"></a>哪些功能是所有網頁瀏覽器都支援的？

- [加入用於控制功能的自訂程式碼](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) (例如屬性、搜尋和播放等候程式等功能)。

- 快顯和對話方塊

- [執行不含傳回型別的基本 JavaScript](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- 搜尋彈性 (使用智慧比對) 和 [performance improvements](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/) (效能改進)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>為什麼應該跨多種 Web 瀏覽器類型使用自動程式化 UI 測試?

您的使用者可能執行不同的瀏覽器，因此使用各種 Web 瀏覽器類型測試 Web 應用程式可以進一步模擬其 UI 使用經驗。 例如，您的應用程式可能會在 Internet Explorer 中包含與其他 Web 瀏覽器不相容的控制項或程式碼。 若能跨其他瀏覽器執行自動程式碼 UI 測試，可以找出並修正任何可能影響客戶的問題。

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>如何使用支援的 Web 瀏覽器，在 Web 應用程式上錄製和播放自動程式化 UI 測試？

**記錄：** 您必須使用自動程式碼 UI 測試產生器，來記錄使用 Internet Explorer 的 Web 應用程式測試。 您可以選擇性地使用一組預先定義的屬性針對待測控制項加入驗證和自訂程式碼，就像平常使用自動程式化 UI 測試所做的一樣。 如需詳細資訊，請參閱 [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)。

> [!NOTE]
> 您不能使用 Google Chrome 或 Mozilla Firefox 瀏覽器記錄自動程式化 UI 測試。

**使用 Internet Explorer 播放：** 若未明確指定瀏覽器，預設會使用 Internet Explorer 執行測試。 您可以在測試程式碼中設定 **BrowserWindow.CurrentBrowser** 屬性，以明確指定要使用的瀏覽器。 若使用 Internet Explorer，應將這個屬性設定為 **IE** 或 **Internet Explorer**。

**使用非 Internet Explorer 網頁瀏覽器播放：** 若要在非 Internet Explorer 的網頁瀏覽器中播放，請將測試程式碼中的 BrowserWindow.CurrentBrowser 屬性變更為 **Firefox** 或 **Chrome**。

若要在非 IE 網頁瀏覽器上播放測試，您必須安裝 **自動程式碼 UI 跨瀏覽器測試專用的 Selenium 元件**。

### <a name="install-selenium-components"></a>安裝 Selenium 元件

::: moniker range="vs-2017"

1. 在 [ **工具** ] 功能表中選擇 [ **擴充功能和更新**]。

2. 在 [擴充功能和更新] 對話方塊中，搜尋 `Selenium components for Cross Browser Testing`。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [擴充功能] 功能表中，選擇 [管理擴充功能]。

2. 在 [管理擴充功能] 對話方塊中，搜尋 `Selenium components for Cross Browser Testing`。

::: moniker-end

3. 反白顯示延伸模組並選擇 [下載]。

    > [!TIP]
    > 您也可以在[這裡](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)下載自動程式碼 UI 跨瀏覽器測試專用的 Selenium 元件。

如需建立和使用自動程式化 UI 測試的詳細資訊，請參閱[建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)。

### <a name="enable-debugging"></a>啟用偵錯

若要啟用偵錯 Web 應用程式的功能，您必須完成下列組態選項：

1. 啟用 Just My Code：

    1. 在 [工具] 功能表中選擇 [選項]，然後選擇 [偵錯]。

    2. 選取 [啟用 Just My Code]。

2. 停用 CLR 例外狀況：

    1. 在 [偵錯] 功能表中選擇 [例外狀況]。

    2. 取消核取 [通用語言執行平台例外狀況] 的 [使用者未處理]。

如果在自動程式化 UI 測試中看不到變更 `BrowserWindow.CurrentBrowser` 的選項，您使用的 Visual Studio 版本可能不支援使用各種網頁瀏覽器進行自動程式化 UI 測試。 若要使用這樣的自動程式化 UI 測試，您必須使用 Visual Studio Enterprise 版。

以下是一些您應該知道的事項：

- 不支援 Apple Safari Web 瀏覽器。

- 自動程式碼 UI 測試必須包含啟動 Web 瀏覽器的動作。

   如果您已開啟一個 Web 瀏覽器，並且想要在其中執行步驟，除非使用 Internet Explorer，否則會播放失敗。 因此，最佳作法是在自動程式化 UI 測試中包含啟動 Web 瀏覽器的動作。

- 不支援自動化瀏覽器架構專用的 UI 動作，例如最大化、最小化和還原。

## <a name="tips"></a>提示

您可以設定輸出，在自動程式碼 UI 記錄中包含螢幕擷取畫面。 若要這麼做，您需要完成 *QTAgent32.exe.config* 檔案的某些組態設定。 根據預設，這個檔案會安裝在下列位置：

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

設定下列值：

- `EqtTraceLevel` 區段中的`system.diagnostics`。

- `<add name="EqtTraceLevel" value="4" />`

   將值設為 3 或以上，即可擷取每一個動作的螢幕擷取畫面。 若將值設為 1 或 2 時，則只擷取錯誤動作的螢幕擷取畫面。

如需詳細資訊，請參閱[使用自動程式化 UI 測試記錄分析自動程式化 UI 測試](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)。

## <a name="video-resources"></a>影片資源

[在 IE 上錄製並隨處播放](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[使用自動程式碼 UI 測試產生器撰寫跨瀏覽器測試](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[使用純手動編碼而不使用 UI 對應撰寫跨瀏覽器的測試](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[循序在多個瀏覽器執行跨瀏覽器的測試](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[針對跨瀏覽器測試失敗問題進行疑難排解](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [使用自動程式碼 UI 測試記錄來分析自動程式碼 UI 測試](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
