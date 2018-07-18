---
title: 疑難排解和已知問題進行偵錯快照集 |Microsoft 文件
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7340b5f6ce7e9f8cbcbb0e2673b22712b3ab45a3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480094"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>快照集，則在 Visual Studio 中偵錯的疑難排解和已知問題

如果本主題中所述的步驟無法解決您的問題，請連絡snaphelp@microsoft.com。

## <a name="issue-snappoint-does-not-turn-on"></a>問題： Snappoint 不會開啟

如果您看到警告圖示![Snappoint 警告圖示](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Snappoint 警告圖示")與您 snappoint 而不是一般 snappoint 圖示，然後 snappoint 未開啟。

![Snappoint 不會開啟](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint 不會開啟")

執行下列步驟：

1. 請確定您具有相同版本的原始碼用來建置和部署您 app.isua1。 請確定您載入正確的符號為您的部署。 若要這樣做，請檢視**模組**視窗偵錯快照集時，並確認您正在偵錯模組載入的符號檔的資料行顯示.pdb 檔案。 請注意，快照集偵錯工具會嘗試自動下載並使用符號為您的部署。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題： 符號不會載入時開啟 快照集

如果您看到下列視窗中，未載入符號。

![未載入符號](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "不載入符號")

執行下列步驟：

- 按一下**變更符號設定...** 此頁面上的連結。 在**偵錯 > 符號**設定，將符號快取目錄。 重新啟動設定符號路徑之後，偵錯快照集。

   符號或在您的專案中可用的.pdb 檔案必須符合您的應用程式服務部署。 大部分的部署 (透過 Visual Studio，CI/CD VSTS 或 Kudu 與部署等) 會將符號檔發行沿著至應用程式服務。 設定符號快取目錄，可讓 Visual Studio 來使用這些符號。

   ![符號設定](../debugger/media/snapshot-troubleshooting-symbol-settings.png "符號設定")

- 或者，如果您的組織使用符號伺服器，或是卸除另一個路徑中的符號，請使用符號設定載入正確的符號為您的部署。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>問題： 我看不在 Cloud Explorer 中的 「 附加快照偵錯工具 」 選項

執行下列步驟：

- 請確定已安裝的快照集偵錯工具元件。 開啟 Visual Studio 安裝程式，並檢查**快照偵錯工具**Azure 的工作負載中的元件。
- 請確定您的應用程式支援。 目前，只有 ASP.NET (4.6.1+) 並支援 ASP.NET Core （2.0 +） 的應用程式部署至 Azure 應用程式服務。

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>問題： 我只能看到節流診斷工具中的快照集

![節流，已 snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "節流 snappoint")

執行下列步驟：

- 快照集佔用很少的記憶體，但沒有認可費用。 如果快照集偵錯工具偵測到您的伺服器是在大量的記憶體負載下，不需要快照集。 您可以刪除已擷取的快照集，停止快照集偵錯工具工作階段並再試一次。

## <a name="known-issues"></a>已知問題

- 目前不支援對相同的應用程式服務的多個 Visual Studio 用戶端使用的快照集進行偵錯。
- Roslyn IL 最佳化不完全支援在 ASP.NET Core 專案。 對於某些 ASP.NET Core 專案，您可能無法看到部分變數，或在條件陳述式中使用一些變數。 
- 特殊變數，例如 *$FUNCTION*或 *$CALLER*，無法評估在條件陳述式或 logpoints ASP.NET Core 專案。
- 偵錯快照集不會對此應用程式服務具有[本機快取](/azure/app-service/app-service-local-cache)開啟。
- 目前不支援偵錯應用程式開發介面應用程式的快照集。

## <a name="site-extension-upgrade"></a>網站擴充功能升級

快照集偵錯和 Application Insights 取決於 ICorProfiler 載入網站處理序，並在升級期間造成檔案鎖定問題。 我們建議此程序，確保沒有任何停機時間生產網站。

- 建立[部署位置](/azure/app-service/web-sites-staged-publishing)應用程式服務中，您的網站部署至該位置。
- 交換生產位置，從 Visual Studio 中的 Cloud Explorer 中，或從 Azure 入口網站。
- 停止位置站台。 這需要幾秒鐘關閉站台 w3wp.exe 處理程序，從所有執行個體終止的時間。
- 升級從 Kudu 網站或 Azure 入口網站的位置的網站擴充功能 (*應用程式服務刀鋒視窗 > 開發工具 > 延伸模組 > 更新*)。
- 啟動位置站台。 我們建議您瀏覽再次準備網站。
- 交換生產位置。

## <a name="see-also"></a>另請參閱

[Visual Studio 偵錯](../debugger/index.md)  
[偵錯即時使用快照集偵錯工具的 ASP.NET 應用程式](../debugger/debug-live-azure-applications.md)  
[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)  
