---
title: 疑難排解 快照集偵錯 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82d8a310b86d5dc3c776243293a91f176025f897
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059823"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>針對快照集偵錯在 Visual Studio 中的疑難排解和已知問題

如果這篇文章中所述的步驟無法解決您的問題，請連絡snaphelp@microsoft.com。

## <a name="issue-snappoint-does-not-turn-on"></a>問題：貼齊點不會開啟

如果您看到警告圖示![貼齊點警告圖示](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "貼齊點警告圖示")與您貼齊點而不是一般的貼齊點圖示，然後貼齊點未開啟。

![貼齊點不會開啟](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "貼齊點不會開啟")

執行下列步驟：

1. 請確定您有相同版本的原始碼，用來建置及部署您 app.isua1。 請確定您正在載入正確的符號，為您的部署。 若要這樣做，請檢視**模組**視窗在快照集偵錯時，並確認已載入模組進行偵錯的符號檔的資料行顯示的.pdb 檔案。 快照集偵錯工具會嘗試自動下載，並為您的部署使用的符號。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題：開啟 快照集時，未載入符號

如果您看到下列視窗中，未載入符號。

![未載入符號](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "未載入符號")

執行下列步驟：

- 按一下 **變更符號設定...** 此頁面上的連結。 在 **偵錯 > 符號**設定，將符號快取目錄。 重新啟動設定符號路徑之後，快照集偵錯。

   符號或在專案中可用的.pdb 檔案必須符合您的 App Service 部署。 大部分的部署 (透過 Visual Studio，搭配 Azure 管線或 Kudu，CI/CD 部署等) 會將沿著您符號檔發行至您的 App Service。 設定符號快取目錄，可讓 Visual Studio 來使用這些符號。

   ![符號設定](../debugger/media/snapshot-troubleshooting-symbol-settings.png "符號設定")

- 或者，如果您的組織使用符號伺服器，或是卸除另一個路徑中的符號，請使用符號設定載入正確的符號，為您的部署。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>問題：我看不到 [雲端總管] 中的 「 附加快照偵錯工具 」 選項

執行下列步驟：

- 請確定已安裝的快照集偵錯工具元件。 開啟 Visual Studio 安裝程式，並檢查**快照集偵錯工具**Azure 工作負載的元件。
- 請確定您的應用程式支援。 目前，只有 ASP.NET (4.6.1+) 並支援 ASP.NET Core （2.0 +） 應用程式部署至 Azure App Service。

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>問題：我只會看到節流診斷工具中的快照集

![節流的貼齊點](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "節流的貼齊點")

執行下列步驟：

- 快照集佔用記憶體少，但沒有確認負載。 如果快照集偵錯工具偵測到您的伺服器是在大量的記憶體負載下，它不會快照集。 您可以停止快照集偵錯工具工作階段，然後再試，以刪除已擷取的快照集。

## <a name="known-issues"></a>已知問題

- 目前不支援針對相同的 App Service 的多個 Visual Studio 用戶端使用的快照集偵錯。
- Roslyn IL 最佳化不完全支援 ASP.NET Core 專案中。 某些 ASP.NET Core 專案中，您可能無法以查看一些變數，或在條件陳述式中使用一些變數。 
- 特殊的變數，例如 *$FUNCTION*或是 *$CALLER*，無法評估在條件陳述式或 ASP.NET Core 專案的記錄點。
- 快照集偵錯不適用於應用程式服務都[本機快取](/azure/app-service/app-service-local-cache)開啟。
- 目前不支援快照集偵錯 API 應用程式。

## <a name="site-extension-upgrade"></a>站台擴充功能升級

快照集偵錯和 Application Insights 相依於 ICorProfiler 載入的站台處理序，並在升級期間造成檔案鎖定的問題。 我們建議此程序，以確保您的生產網站沒有停機時間。

- 建立[部署位置](/azure/app-service/web-sites-staged-publishing)在您的應用程式服務並將您的網站部署至位置。
- 從 Visual Studio 中的 Cloud Explorer，或從 Azure 入口網站，交換與生產環境位置。
- 停止位置的站台。 這需要幾秒鐘才會關閉所有執行個體中的站台 w3wp.exe 處理序終止。
- 從 Kudu 網站或 Azure 入口網站中升級位置的網站延伸模組 (*應用程式服務 刀鋒視窗 > 開發工具 > 擴充功能 > 更新*)。
- 開始位置的站台。 我們建議您瀏覽的網站，再進行準備。
- 交換生產位置。

## <a name="see-also"></a>另請參閱

[Visual Studio 偵錯](../debugger/index.md)  
[使用快照集偵錯工具的即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)  
[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)  
