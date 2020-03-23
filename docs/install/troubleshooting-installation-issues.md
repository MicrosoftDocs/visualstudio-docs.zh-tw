---
title: 針對安裝或升級問題進行疑難排解
description: 有時可能會發生一些問題。 如果您的 Visual Studio 安裝或升級失敗，則這個頁面會有所幫助。
ms.date: 09/13/2019
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9dfdf504378dafd7d71288cae1927dd8d6bb9e56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115006"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>針對 Visual Studio 安裝和升級問題進行疑難排解

> [!IMPORTANT]
> 遇到安裝問題嗎？ 我們可以幫您。 我們提供[**即時交談**](https://visualstudio.microsoft.com/vs/support/#talktous) (僅限英文) 支援選項。

此疑難排解指南包括逐步指示，應該可以解決大部分的安裝問題。

## <a name="online-installations"></a>線上安裝

下列步驟已針對傳統線上安裝最佳化。 針對影響離線安裝的問題，請參閱 [如何針對離線安裝進行疑難排解](#offline-installations)。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>步驟 1 - 查看此問題是否為已知問題

::: moniker range="vs-2017"

Visual Studio 安裝程式有一些已知問題，Microsoft 正在努力修正。 若要查看是否有您問題的因應措施，請參閱[版本資訊的＜已知問題＞一節](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 安裝程式有一些已知問題，Microsoft 正在努力修正。 若要查看是否有您問題的因應措施，請參閱[版本資訊的＜已知問題＞一節](/visualstudio/releases/2019/release-notes#-known-issues)。

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>步驟 2 - 查看開發人員社群

在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)\(英文\) 中搜尋您的錯誤訊息。 社群的其他成員可能已記錄您問題的解決方式。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題

Visual Studio 安裝程式啟動載入器是最小的輕量型可執行檔，可安裝 Visual Studio 安裝程式的其餘部分。 刪除 Visual Studio 安裝程式檔案，然後重新執行啟動載入器，可能可以解決一些更新失敗問題。

> [!NOTE]
> 執行下列動作將會重新安裝 Visual Studio 安裝程式檔案並重設安裝中繼資料。

::: moniker range="vs-2017"

1. 關閉 Visual Studio 安裝程式。
2. 刪除 Visual Studio 安裝程式目錄。 此目錄通常是 `C:\Program Files (x86)\Microsoft Visual Studio\Installer`。
3. 執行 Visual Studio 安裝程式啟動載入器。 您可以在 [下載] 資料夾中找到檔名遵循 `vs_[Visual Studio edition]__*.exe` 模式的啟動載入器。 如果您找不到該應用程式，您可以通過轉到[Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面並按一下"下載"為您的版 Visual Studio 下載**Download**來下載引導器。 接著，執行該可執行檔來重設您的安裝中繼資料。
4. 嘗試重新安裝或更新 Visual Studio。 如果安裝程式持續失敗，請移至下一步驟。

::: moniker-end

::: moniker range="vs-2019"

1. 關閉 Visual Studio 安裝程式。
2. 刪除 Visual Studio 安裝程式目錄。 此目錄通常是 `C:\Program Files (x86)\Microsoft Visual Studio\Installer`。
3. 執行 Visual Studio 安裝程式啟動載入器。 您可以在 [下載] 資料夾中找到檔名遵循 `vs_[Visual Studio edition]__*.exe` 模式的啟動載入器。 如果您找不到該應用程式，您可以通過轉到[Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面並按一下"下載"為您的版 Visual Studio 下載**Download**來下載引導器。 接著，執行該可執行檔來重設您的安裝中繼資料。
4. 嘗試重新安裝或更新 Visual Studio。 如果安裝程式持續失敗，請移至下一步驟。

::: moniker-end

### <a name="step-4---report-a-problem"></a>步驟 4 - 回報問題

在某些情況下 (例如與損毀的檔案相關的問題)，則必須逐一查看問題。 為了幫助我們幫助您，請執行下列動作：

::: moniker range="vs-2017"

1. 收集您的安裝記錄檔。 如需詳細資訊，請參閱[如何取得 Visual Studio 安裝記錄檔](#installation-logs)。
2. 開啟 Visual Studio 安裝程式，然後按一下 [回報問題]**** 以開啟「Visual Studio 意見反應」工具。
![您可以使用 Tab 鍵移至 [提供意見反應] 按鈕以開啟意見反應工具](media/report-a-problem.png)
3. 提供問題報告標題，並提供相關詳細資料。 按一下 [下一步]**** 以移至 [附件]**** 區段，然後附加產生的記錄檔 (一般而言，該檔案位於 `%TEMP%\vslogs.zip`)。
4. 按一下 [下一步]**** 以檢閱您的問題報告，然後按一下 [提交]****。

::: moniker-end

::: moniker range="vs-2019"

1. 收集您的安裝記錄檔。 如需詳細資訊，請參閱[如何取得 Visual Studio 安裝記錄檔](#installation-logs)。
2. 開啟 Visual Studio 安裝程式，然後按一下 [回報問題]**** 以開啟「Visual Studio 意見反應」工具。
![您可以使用 Tab 鍵移至 [提供意見反應] 按鈕以開啟意見反應工具](media/vs-2019/vs-installer-report-problem.png)
3. 提供問題報告標題，並提供相關詳細資料。 按一下 [下一步]**** 以移至 [附件]**** 區段，然後附加產生的記錄檔 (一般而言，該檔案位於 `%TEMP%\vslogs.zip`)。
4. 按一下 [下一步]**** 以檢閱您的問題報告，然後按一下 [提交]****。

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>步驟 5 - 執行 InstallCleanup.exe 以移除安裝檔案

非不得已，您可以[移除 Visual Studio](remove-visual-studio.md)來移除所有安裝檔案和產品資訊。

1. 請遵循[移除 Visual Studio](remove-visual-studio.md) 中的指示進行。
2. 重新執行[步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)中所述的啟動載入器。
3. 嘗試重新安裝或更新 Visual Studio。

### <a name="step-6---contact-us-optional"></a>步驟 6 - 與我們連絡 (選擇性)

若上述步驟都無法協助您成功地安裝或升級 Visual Studio，請使用我們的[**即時聊天**](https://visualstudio.microsoft.com/vs/support/#talktous)支援選項 (僅限英文) 與我們連絡以取得進一步的協助。

## <a name="offline-installations"></a>離線安裝

下面是一個已知問題和一些解決方法的表，這些解決方法在創建[離線安裝](create-an-offline-installation-of-visual-studio.md)然後從本地佈局安裝時可能會有所説明。

| 問題       | Item                   | 解決方法 |
| ----------- | ---------------------- | -------- |
| 使用者沒有檔案的存取權。 | 權限 (ACL) | 請確保調整許可權 （ACL），以便在共用離線安裝*之前*，這些許可權（ACL）會向其他使用者授予 Read 存取權限。 |
| 無法安裝新的工作負載、元件或語言。  | `--layout`  | 如果是以部分配置來安裝，並選取該部分配置中先前未下載的工作負載、元件或語言，請確定可以存取網際網路。 |

有關如何解決[網路安裝](create-a-network-installation-of-visual-studio.md)問題的詳細資訊，請參閱[安裝或使用 Visual Studio 時排除與網路相關的錯誤](troubleshooting-network-related-errors-in-visual-studio.md)。

## <a name="installation-logs"></a>安裝日誌

針對大部分安裝問題進行疑難排解時，將會需要安裝記錄檔。 使用 Visual Studio 安裝程式中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio.md)來提交問題時，會自動將這些記錄檔包含在報告中。

當您連絡 Microsoft 支援服務時，可能需要使用 [Microsoft Visual Studio 與 .NET Framework 記錄收集工具](https://www.microsoft.com/download/details.aspx?id=12493) \(英文\) 來提供這些安裝記錄檔。 記錄收集工具會收集來自 Visual Studio 所安裝之所有元件的安裝記錄，包括 .NET Framework、Windows SDK 及 SQL Server。 它也會收集電腦資訊、Windows Installer 詳細目錄與 Windows 事件記錄檔資訊，以供 Visual Studio 安裝程式、Windows Installer 與系統還原使用。

若要收集記錄檔：

1. [下載該工具](https://www.microsoft.com/download/details.aspx?id=12493)。
2. 開啟系統管理命令提示字元。
3. 從儲存工具的目錄執行 `Collect.exe`。
4. 在您的 `%TEMP%` 目錄中尋找產生的 `vslogs.zip` 檔案，例如 `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`。

> [!NOTE]
> 執行工具所用的帳戶，必須相同於執行失敗安裝所用的帳戶。 如果使用不同的使用者帳戶來執行工具，請設定 `–user:<name>` 選項，以指定執行失敗安裝所用的使用者帳戶。 如需其他選項與使用資訊，請從系統管理命令提示字元執行 `Collect.exe -?`。

## <a name="live-help"></a>現場説明

若此疑難排解指南中所列的解決方式無法協助您成功地安裝或升級 Visual Studio，請使用我們的[**即時聊天**](https://visualstudio.microsoft.com/vs/support/#talktous)支援選項 (僅限英文) 以取得進一步的協助。

## <a name="see-also"></a>另請參閱

* [移除 Visual Studio](remove-visual-studio.md)
* [在防火牆或 Proxy 伺服器後方安裝並使用 Visual Studio 和 Azure 服務](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
