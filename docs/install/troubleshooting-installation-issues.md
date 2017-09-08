---
title: "針對安裝問題進行疑難排解 | Microsoft Docs"
description: "有時可能會發生一些問題。 如果您的 Visual Studio 安裝或升級失敗，則這個頁面會有所幫助。"
ms.date: 08/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6f0fe07b55ae0eeb57c0cc11fed047f31966cb6e
ms.openlocfilehash: 15e3b7cf051d26b6784df13f57794f6057e4c91c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>針對 Visual Studio 2017 安裝和升級問題進行疑難排解

## <a name="symptoms"></a>徵兆
當您嘗試安裝或更新 Visual Studio 2017 時，作業會失敗。

## <a name="workaround"></a>因應措施
若要暫時解決此問題，請依照這些步驟執行。

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>步驟 1 - 查看此問題是否為已知問題
Visual Studio 安裝程式有一些已知問題，Microsoft 正在努力修正。 查看[我們版本資訊的已知問題區段](https://www.visualstudio.com/news/releasenotes/vs2017-knownissues)，看看是否有您問題的因應措施。

### <a name="step-2---check-with-the-developer-community"></a>步驟 2 - 查看開發人員社群
在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)\(英文\) 中搜尋您的錯誤訊息。 社群的其他成員可能已記錄您問題的解決方案。

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題
Visual Studio 安裝程式啟動載入器是最小的輕量型可執行檔，可安裝 Visual Studio 安裝程式的其餘部分。 刪除 Visual Studio 安裝程式檔案，然後重新執行啟動載入器，可能可以解決一些更新失敗問題。

**注意：**執行下列動作將會重新安裝 Visual Studio 安裝程式檔案並重設安裝中繼資料。

1. 關閉 Visual Studio 安裝程式。
2. 刪除 Visual Studio 安裝程式目錄。 一般而言，目錄為 C:\Program Files (x86)\Microsoft Visual Studio\Installer。
3. 執行 Visual Studio 安裝程式啟動載入器。 您可在 [下載] 資料夾中找到檔名遵循 ```vs_[Visual Studio edition]__*.exe``` 模式的啟動載入器。 如果找不到該應用程式，請移至 [Visual Studio 下載](https://www.visualstudio.com/downloads/)頁面並按一下您 Visual Studio 版本的 [下載] 來下載啟動載入器。 執行該可執行檔來重設您的安裝中繼資料。
4. 嘗試重新安裝或更新 Visual Studio。 如果安裝程式持續失敗，請移至下一步驟。

### <a name="step-4---report-a-problem"></a>步驟 4 - 回報問題
在某些情況下 (例如與損毀的檔案相關的問題)，則必須逐一查看問題：

1. 收集您的安裝記錄檔。 如需詳細資訊，請參閱以下的[如何取得 Visual Studio 安裝記錄檔](#how-to-get-the-visual-studio-installation-logs)。
2. 開啟 Visual Studio 安裝程式，然後按一下 [回報問題] 以開啟「Visual Studio 意見反應」工具。
![您可以使用 Tab 鍵移至 [提供意見反應] 按鈕以開啟意見反應工具](media/report-a-problem.png)
3. 提供問題報告標題，並提供相關詳細資料。 按一下 [下一步] 以移至 [附件] 區段，然後附加產生的記錄檔 (一般而言，該檔案位於 %TEMP%\vslogs.zip)。
![使用 Tab 鍵移至 [回報新問題]，然後依照步驟執行](media/problem-report-details.png)
4. 按一下 [下一步] 以檢閱您的問題報告，然後按一下 [提交]。

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>步驟 5 - 執行 InstallCleanup.exe 以清除安裝檔案
作為最後一個手段，您可以執行 InstallCleanup.exe。 InstallCleanup.exe 是隨 Visual Studio 安裝程式封裝的工具，可清除安裝檔案。 此工具不會執行完整重新安裝。 此工具會刪除 Visual Studio 2017 的快取和執行個體資料。

1. 關閉 Visual Studio 安裝程式。
2. 開啟系統管理員命令提示字元。 若要執行此動作，請依照下列步驟執行：
   * 在 [開始] 功能表上，按一下 [執行] (開始 + R)。
   * 輸入 **cmd**。
   * 以右鍵按一下 [命令提示字元]，然後選擇 [以系統管理員身分執行]。
3. 輸入 InstallCleanup.exe 公用程式的完整路徑，並傳遞下列命令列參數：-f。 根據預設，公用程式的路徑如下所示：
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. 重新執行[步驟 3 - 刪除 Visual Studio 安裝程式目錄，以修正升級問題](#step-3--delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)中所述的啟動載入器。
5. 嘗試重新安裝或更新 Visual Studio。

## <a name="how-to-troubleshoot-an-offline-installer"></a>如何針對離線安裝程式進行疑難排解
下表是從本機配置進行安裝時的已知問題，及一些可能有幫助的因應措施。

| 問題       | 項目                   | 解決方式 |
| ----------- | ---------------------- | -------- |
| 使用者沒有檔案的存取權。 | 權限 (ACL) | 請務必在您共用離線安裝「之前」調整權限 (ACL)，讓它們將「讀取權」授與其他使用者。 |
| 無法安裝新的工作負載、元件或語言。  | `--layout`  | 如果是以部分配置來安裝，並選取該部分配置中先前未下載的工作負載、元件或語言，請確定可以存取網際網路。 |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>如何取得 Visual Studio 安裝記錄檔
針對大部分安裝問題進行疑難排解時，將會需要安裝記錄檔。 使用 Visual Studio 安裝程式中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)來提交問題時，會自動將這些記錄檔包含在報告中。

當您連絡 Microsoft 支援服務時，可能需要使用 [Microsoft Visual Studio 與 .NET Framework 記錄收集工具](https://aka.ms/vscollect) \(英文\) 來提供這些安裝記錄檔。 記錄收集工具會收集 Visual Studio 2017 所安裝全部元件的安裝記錄檔，包括 .NET Framework、Windows SDK，以及 SQL Server。 它也會收集電腦資訊、Windows Installer 詳細目錄與 Windows 事件記錄檔資訊，以供 Visual Studio 安裝程式、Windows Installer 與系統還原使用。

收集記錄檔

1. [下載工具](https://aka.ms/vscollect) \(英文\)。
2. 開啟系統管理命令提示字元。
3. 從儲存工具的目錄執行 Collect.exe。
4. 在 %TEMP% 目錄中，找出所產生的 Vslogs.zip 檔案，例如，C:\Users\YourName\AppData\Local\Temp\vslogs.zip。

> [!NOTE]
> 執行工具所用的帳戶，必須相同於執行失敗安裝所用的帳戶。 如果使用不同的使用者帳戶來執行工具，請設定 -user:\<名稱\> 選項，以指定執行失敗安裝所用的使用者帳戶。 如需其他選項與使用資訊，請從系統管理命令提示字元執行 `Collect.exe -?`。

