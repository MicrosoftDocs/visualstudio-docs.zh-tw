---
title: 針對 Visual Studio 2017 的安裝問題進行疑難排解
description: 有時可能會發生一些問題。 如果您的 Visual Studio 安裝或升級失敗，則這個頁面會有所幫助。
ms.date: 11/21/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02ed2724f82923ed2157133c3c36b9ff06a1b7d5
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282950"
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>針對 Visual Studio 2017 安裝和升級問題進行疑難排解

## <a name="symptoms"></a>徵兆

當您嘗試安裝或更新 Visual Studio 2017 時，作業會失敗。

## <a name="workaround"></a>因應措施

若要暫時解決此問題，請依照這些步驟執行。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>步驟 1 - 查看此問題是否為已知問題

Visual Studio 安裝程式有一些已知問題，Microsoft 正在努力修正。 若要查看是否有您問題的因應措施，請參閱[版本資訊的＜已知問題＞一節](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)。

### <a name="step-2---check-with-the-developer-community"></a>步驟 2 - 查看開發人員社群

在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)\(英文\) 中搜尋您的錯誤訊息。 社群的其他成員可能已記錄您問題的解決方案。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題

Visual Studio 安裝程式啟動載入器是最小的輕量型可執行檔，可安裝 Visual Studio 安裝程式的其餘部分。 刪除 Visual Studio 安裝程式檔案，然後重新執行啟動載入器，可能可以解決一些更新失敗問題。

>[!NOTE]
執行下列動作將會重新安裝 Visual Studio 安裝程式檔案並重設安裝中繼資料。

1. 關閉 Visual Studio 安裝程式。
2. 刪除 Visual Studio 安裝程式目錄。 此目錄通常是 `C:\Program Files (x86)\Microsoft Visual Studio\Installer`。
3. 執行 Visual Studio 安裝程式啟動載入器。 您可在 [下載] 資料夾中找到檔名遵循 `vs_[Visual Studio edition]__*.exe` 模式的啟動載入器。 如果找不到該應用程式，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面並按一下您 Visual Studio 版本的 [下載] 來下載啟動載入器。 執行該可執行檔來重設您的安裝中繼資料。
4. 嘗試重新安裝或更新 Visual Studio。 如果安裝程式持續失敗，請移至下一步驟。

### <a name="step-4---report-a-problem"></a>步驟 4 - 回報問題

在某些情況下 (例如與損毀的檔案相關的問題)，則必須逐一查看問題：

1. 收集您的安裝記錄檔。 如需詳細資訊，請參閱[如何取得 Visual Studio 安裝記錄檔](#how-to-get-the-visual-studio-installation-logs)。
2. 開啟 Visual Studio 安裝程式，然後按一下 [回報問題] 以開啟「Visual Studio 意見反應」工具。
![您可以使用 Tab 鍵移至 [提供意見反應] 按鈕以開啟意見反應工具](media/report-a-problem.png)
3. 提供問題報告標題，並提供相關詳細資料。 按一下 [下一步] 以移至 [附件] 區段，然後附加產生的記錄檔 (一般而言，該檔案位於 `%TEMP%\vslogs.zip`)。
4. 按一下 [下一步] 以檢閱您的問題報告，然後按一下 [提交]。

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>步驟 5 - 執行 InstallCleanup.exe 以移除安裝檔案

非不得已，您可以[移除 Visual Studio](remove-visual-studio.md)來移除所有安裝檔案和產品資訊。

1. 請遵循[移除 Visual Studio](remove-visual-studio.md) 中的指示進行。
2. 重新執行[步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)中所述的啟動載入器。
3. 嘗試重新安裝或更新 Visual Studio。

### <a name="step-6---contact-us-optional"></a>步驟 6 - 與我們連絡 (選擇性)

如果其他步驟都無法讓您成功安裝，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資料，請參閱 [Visual Studio 支援頁面](https://visualstudio.microsoft.com/vs/support/#talktous)。

## <a name="how-to-troubleshoot-an-offline-installer"></a>如何針對離線安裝程式進行疑難排解

下表是從本機配置進行安裝時的已知問題，及一些可能有幫助的因應措施。

| 問題       | 項目                   | 方案 |
| ----------- | ---------------------- | -------- |
| 使用者沒有檔案的存取權。 | 權限 (ACL) | 請務必在您共用離線安裝「之前」調整權限 (ACL)，讓它們將「讀取權」授與其他使用者。 |
| 無法安裝新的工作負載、元件或語言。  | `--layout`  | 如果是以部分配置來安裝，並選取該部分配置中先前未下載的工作負載、元件或語言，請確定可以存取網際網路。 |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>如何取得 Visual Studio 安裝記錄檔

針對大部分安裝問題進行疑難排解時，將會需要安裝記錄檔。 使用 Visual Studio 安裝程式中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)來提交問題時，會自動將這些記錄檔包含在報告中。

當您連絡 Microsoft 支援服務時，可能需要使用 [Microsoft Visual Studio 與 .NET Framework 記錄收集工具](https://aka.ms/vscollect) \(英文\) 來提供這些安裝記錄檔。 記錄收集工具會收集 Visual Studio 2017 所安裝全部元件的安裝記錄檔，包括 .NET Framework、Windows SDK，以及 SQL Server。 它也會收集電腦資訊、Windows Installer 詳細目錄與 Windows 事件記錄檔資訊，以供 Visual Studio 安裝程式、Windows Installer 與系統還原使用。

若要收集記錄檔：

1. [下載工具](https://aka.ms/vscollect) \(英文\)。
2. 開啟系統管理命令提示字元。
3. 從儲存工具的目錄執行 `Collect.exe`。
4. 在您的 `%TEMP%` 目錄中尋找產生的 `vslogs.zip` 檔案，例如 `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`。

> [!NOTE]
> 執行工具所用的帳戶，必須相同於執行失敗安裝所用的帳戶。 如果使用不同的使用者帳戶來執行工具，請設定 `–user:<name>` 選項，以指定執行失敗安裝所用的使用者帳戶。 如需其他選項與使用資訊，請從系統管理命令提示字元執行 `Collect.exe -?`。

## <a name="more-support-options"></a>更多支援選項

如果其他步驟都無法讓您成功安裝，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資料，請參閱 [Visual Studio 支援頁面](https://visualstudio.microsoft.com/vs/support/#talktous)。

以下是一些選項：

* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以追蹤產品問題並在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 中尋找解答。
* 您也可以透過[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動。 (這需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱

* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [將 Visual Studio 安裝在防火牆或 Proxy 伺服器後方](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [移除 Visual Studio 2017](remove-visual-studio.md)
