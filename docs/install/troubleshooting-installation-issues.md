---
title: "針對安裝問題進行疑難排解 | Microsoft Docs"
description: "有時可能會發生一些問題。 如果您的 Visual Studio 安裝或升級失敗，則這個頁面會有所幫助。"
ms.date: 04/14/2017
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
ms.sourcegitcommit: 89f86a5935ad283ef5c0e29ea2db0ae22cf603a8
ms.openlocfilehash: 0fd361edd5bc5056f09c64aa4499a10a50656546
ms.contentlocale: zh-tw
ms.lasthandoff: 08/07/2017

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

1. 下載 [ Microsoft Visual Studio and the .NET Framework Log Collection Tool (Microsoft Visual Studio 和 .NET Framework 記錄收集工具)](https://aka.ms/vscollect)，然後執行它。 此工具會收集及編譯適用於 Visual Studio、.NET Framework 和 SQL Server 安裝的可用安裝程式記錄檔。
2. 開啟 Visual Studio 安裝程式，然後按一下 [回報問題] 以開啟「Visual Studio 意見反應」工具。
![您可以使用 Tab 鍵移至 [提供意見反應] 按鈕以開啟意見反應工具](media/report-a-problem.png)
3. 提供問題報告標題，並提供相關詳細資料。 按一下 [下一步] 以移至 [附件] 區段，然後附加產生的記錄檔 (一般而言，該檔案位於 %TEMP%\vslogs.zip)。
![使用 Tab 鍵移至 [回報新問題]，然後依照步驟執行](media/problem-report-details.png)
4. 按一下 [下一步] 以檢閱您的問題報告，然後按一下 [提交]。

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>步驟 5 - 執行 InstallCleanup.exe 以清除安裝檔案
作為最後一個手段，您可以執行 InstallCleanup.exe。 InstallCleanup.exe 是隨 Visual Studio 安裝程式封裝的公用程式，它會清除安裝檔案。 這不是完整的重新安裝。 此公用程式會刪除 Visual Studio 2017 的快取和執行個體資料。

1. 關閉 Visual Studio 安裝程式。
2. 開啟系統管理員命令提示字元。 若要執行此動作，請依照下列步驟執行：
   * 在 [開始] 功能表上，按一下 [執行] (開始 + R)。
   * 輸入 **cmd**。
   * 以右鍵按一下 [命令提示字元]，然後選擇 [以系統管理員身分執行]。
3. 輸入 InstallCleanup.exe 公用程式的完整路徑，並傳遞下列命令列參數：-f。 根據預設，公用程式的路徑如下所示：
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. 重新執行步驟 3 中所述的啟動載入器。
5. 嘗試重新安裝或更新 Visual Studio。

## <a name="how-to-troubleshoot-an-offline-installer"></a>如何針對離線安裝程式進行疑難排解
下表是從本機配置進行安裝時的已知問題，及一些可能有幫助的因應措施。

| 問題       | 項目                   | 解決方式 |
| ----------- | ---------------------- | -------- |
| 使用者沒有檔案的存取權。 | 權限 (ACL) | 請務必在您共用離線安裝「之前」調整權限 (ACL)，讓它們將「讀取權」授與其他使用者。 |
| 無法安裝新的工作負載、元件或語言。  | `--layout`  | 如果您要從某個部分配置安裝，請確定您能夠存取網際網路，然後選取先前配置中沒有的工作負載、元件或語言。 |

