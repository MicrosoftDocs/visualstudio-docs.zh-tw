---
title: 如何增加解決性能問題的機會
description: 在視覺化工作室中提交性能問題的其他資訊和最佳實踐
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: 119de27298acafee7dc563a30246b18da42f9f29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918167"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>如何增加解決性能問題的機會

Visual Studio 使用者廣泛使用"[報告問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)"工具來報告一系列問題。 Visual Studio 團隊發現使用者回饋的崩潰和緩慢趨勢，並解決影響廣大使用者的問題。 特定回饋票證越可操作，產品團隊就越有可能快速診斷和解決該回饋票證。 本文檔介紹了在報告崩潰或慢速問題時最佳做法，使其更具可操作性。

## <a name="general-best-practices"></a>一般最佳作法

Visual Studio 是一個大型的複雜平臺，支援多種語言、專案類型、平臺等。 它的性能是一個功能，用於在會話中安裝和處於活動狀態的元件、安裝的擴展、Visual Studio 設置、電腦配置，以及最後編輯的代碼的形狀。 鑒於變數數，很難判斷來自一個使用者的問題報告與其他使用者的問題報告具有相同的基礎問題，即使可見症狀相同。 因此，下面是一些最佳做法，以確保您的特定問題報告更有可能被診斷。

**提供盡可能具體的標題**

查找所報告問題的不同簽名，並盡可能在標題中包括。 如果標題是描述性的，則出現不相關問題（但相同的表面症狀）的使用者不太可能對您的票證進行投票或評論，從而使診斷*您的*問題更加困難。

**有疑問時，請記錄新問題報告**

許多問題可能沒有任何獨特的簽名或步驟重現。 在這種情況下，新的報告比對另一份報告的投票結果或評論要好，該報告報告有類似的外在*症狀*。 根據報表的類型，將其他診斷檔包含在報表中，如本文檔後面所述。

**特定于問題的最佳做法**

下面描述的問題，很難診斷沒有良好的診斷檔。 確定最能描述您的問題的情況後，請按照特定于該案例的回饋步驟操作。

-   [崩潰：](#crashes)當進程（視覺化工作室）意外終止時，將發生崩潰。

-   [無回應：](#unresponsiveness)VS 在較長時間內變得無回應。

-   [慢速問題：](#slowness-and-high-cpu-issues)VS 中的任何特定操作都比預期慢

-   [高 CPU：](#slowness-and-high-cpu-issues)時間過長的意外高 CPU 使用率

-   [進程外問題：](#out-of-process-issues)由視覺工作室衛星進程引起的問題

## <a name="crashes"></a>損毀
當進程（視覺化工作室）意外終止時，將發生崩潰。

**直接重現崩潰**

直接可重現的崩潰是具有以下所有特徵的案例：

- 可以通過執行一組已知的步驟來觀察

- 可在多台電腦上觀察到（如果可用）

- 可以在示例代碼或專案中複製，該代碼或專案可以連結到回饋或作為回饋的一部分提供（如果步驟涉及打開專案或文檔）

對於這些問題，請按照"[如何報告問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)"中的步驟操作，並確保包括：

-   重現問題的步驟

-   如上所述的獨立重現專案。 如果無法獨立重新進行，請包括：

    -   開放專案的語言（C、C++\#等）

    -   專案類型（主控台應用程式、ASP.NET等）


> [!NOTE]
> **最有價值的回饋：** 在這種情況下，最有價值的回饋是複製問題以及示例原始程式碼的步驟集。

**未知崩潰**

如果您不確定導致崩潰的原因或它們看起來是隨機的，則可以在每次 Visual Studio 崩潰時在本地捕獲轉儲，並將這些轉儲附加到單獨的回饋專案。 要在 Visual Studio 崩潰時在本地保存轉儲，在管理員命令視窗中運行以下命令：

```
reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\\CrashDumps"
```

根據需要自訂轉儲計數和轉儲資料夾。 [在此處](/windows/win32/wer/collecting-user-mode-dumps)查找有關這些設置的詳細資訊。

> [!NOTE]
> 使用工作管理員捕獲的轉儲可能是錯誤的位，這使得它們使用得更少。 上述過程是捕獲堆轉儲的首選方法。 如果確實要使用工作管理員，關閉當前正在運行的工作管理員，啟動 32 位工作管理員（%windir%\\syswow64\\taskmgr.exe），並從那裡收集堆轉儲。

> [!NOTE] 
> 此方法生成的每個轉儲檔的大小將高達 4 GB。 請確保將轉儲資料夾設置為具有足夠磁碟機空間的位置，或適當調整轉儲計數。

每次 Visual Studio 崩潰時，它都會創建轉儲檔**devenv.exe。數位_dmp**檔在配置的位置。

然後，使用視覺化工作室的"報告問題..."特徵。 它允許您附加相應的轉儲。

1.  查找要報告的崩潰的轉儲檔（查找具有正確創建時間的檔）

2.  如果可能，在提交回饋之前\*壓縮檔 （.zip） 以減小其大小

3.  按照"[如何報告問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)"中的步驟操作，並將堆轉儲附加到新的回饋項。

> [!NOTE] 
> **最有價值的回饋：** 對於這種情況，最有價值的回饋是在崩潰時捕獲的堆轉儲。

## <a name="unresponsiveness"></a>無回應
VS 在較長時間內變得無回應。

**直接重現無回應**

如有關崩潰的相應部分所述，對於易於重現、在多台電腦上看到且可在小樣本中演示的問題，最有價值的回饋報告包括重現問題的步驟，包括演示問題的示例原始程式碼。

**未知無回應**

如果無回應以不可預知的方式表現出來，則在下一次發生時，啟動 Visual Studio 的新實例並報告該實例中的問題。
在["錄製"螢幕](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)中，請確保選擇無回應的視覺化工作室會話。

如果在管理員模式下啟動無回應的 Visual Studio 實例，則第二個實例也需要在管理員模式下啟動。

>[!NOTE] 
> **最有價值的回饋：** 對於這種情況，最有價值的回饋是在無回應時捕獲的堆轉儲。

## <a name="slowness-and-high-cpu-issues"></a>速度慢和 CPU 問題高

使速度緩慢或 CPU 使用率高的問題最可操作的是，在操作緩慢或 CPU 事件正在進行時捕獲的性能跟蹤。

>[!NOTE] 
> 如果可能，在單獨的特定回饋報告中隔離每個方案。
例如，如果鍵入和導航速度都很慢，請按問題執行以下步驟一次。 這有助於產品團隊隔離特定問題的原因。

為了獲得最佳捕獲性能的結果，請按照以下步驟操作：

1.  如果尚未運行，請打開 Visual Studio 的副本，在其中重現問題

    -   設置一切以重現問題。 例如，如果需要使用打開的特定檔載入特定專案，請確保這兩個步驟都已完成，然後再繼續。

    -   如果未*報告特定于*載入解決方案的問題，請嘗試在打開解決方案後等待 5-10 分鐘（或更多），然後再記錄性能跟蹤。 解決方案載入過程會產生大量資料，因此等待幾分鐘有助於我們專注于您報告的特定問題。

2.  啟動 Visual Studio 的第二個副本 *，無需打開解決方案*

3.  在 Visual Studio 的新副本中，打開 **"報告問題**"工具

4.  按照["如何報告問題"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)中的步驟操作，直到達到"提供跟蹤和堆轉儲（可選）"步驟。

5.  選擇錄製 Visual Studio 的第一個副本（遇到性能問題的拷貝）並開始錄製。

    -   步驟記錄器應用程式將顯示並開始錄製。

    -   **在錄製過程中，** 在 Visual Studio 的第一個副本中執行有問題的操作。 如果特定性能問題未在記錄的時間內出現，我們很難糾正這些問題。

    -   如果操作短于 30 秒，並且可以輕鬆重複，請重複該操作以進一步演示問題。

    -   在大多數情況下，60 秒的痕跡足以證明問題，特別是如果有問題的操作持續（或重複）超過 30 秒。 可以根據需要調整持續時間，以捕獲要修復的行為。

6.  一旦要報告的慢速操作或高 CPU 事件完成，按一下"步驟記錄器"中的"停止記錄"。 處理性能跟蹤可能需要幾分鐘時間。

7.  完成後，您的回饋將包含多個附件。 附加可能有助於重現問題的任何其他檔（示例專案、螢幕截圖、視頻等）。

8.  提交回饋。

錄製性能跟蹤時，如果報告操作緩慢或 CPU 高結束，則立即停止錄製。 如果收集了太多資訊，則最舊的資訊將被覆蓋。 如果在有趣的操作後（幾秒鐘內）沒有停止跟蹤，則有用的跟蹤資料將被覆蓋。

不要直接將性能跟蹤附加到開發人員社區網站上的現有回饋專案。 請求/提供其他資訊是 Visual Studio 的內置"報告問題"工具中支援的工作流。 如果需要性能跟蹤來解決以前的回饋專案，我們將回饋項的狀態設置為"需要更多資訊"，該狀態可以回應與報告新問題相同的方式。 有關詳細說明，請參閱"報告問題"工具文檔中的["需要更多資訊"部分](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info)。

> [!NOTE] 
> **最有價值的回饋：** 對於幾乎所有速度緩慢/CPU 高的問題，最有價值的回饋是您嘗試做什麼的高級描述，以及捕獲該期間行為的性能跟蹤 （.etl.zip）。\*

**高級性能跟蹤**

"報告問題"工具中的跟蹤收集功能對於大多數方案都足夠。 但是，有時需要對跟蹤集合進行更多的控制（例如，緩衝區大小的跟蹤），在這種情況下，PerfView 是一個偉大的工具。 使用 PerfView 工具手動錄製性能跟蹤的步驟，請參閱[PerfView 頁面的錄製性能跟蹤](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)。

## <a name="out-of-process-issues"></a>進程外問題

> [!NOTE]
> 從 Visual Studio 2019 版本 16.3 開始，進程外日誌將自動附加到使用"報告問題"工具提交的回饋。 但是，如果問題可以直接重現，則按照以下步驟執行以下步驟仍有助於添加其他資訊以説明更好地診斷問題。

有許多衛星進程與 Visual Studio 並行運行，並提供來自主視覺工作室進程之外的各種功能。 如果其中一個衛星進程發生錯誤，通常在視覺工作室一側被視為"StreamJsonRpc.遠端調用異常"或"StreamJsonRpc.連接丟失異常"。

使這些類型的問題最可操作的是提供其他日誌，可以通過以下步驟收集：

1.  如果這是直接可重現的問題，則從刪除 **%temp%/servicehub/logs**資料夾開始。 如果無法重現此問題，請保持此資料夾完好無損並忽略以下專案符號：

    -   將全域環境變數**ServiceHub 跟蹤級別**設置為**全部**
    -   重現問題。

2.  [在此處](https://www.microsoft.com/download/details.aspx?id=12493)下載微軟視覺工作室和 .NET 框架日誌收集工具。
3.  執行工具。 這將 ZIP 檔案輸出到 **%temp%/vslogs.zip**。 請將該檔附加到您的回饋中。

## <a name="see-also"></a>另請參閱

* [Visual Studio 意見反應選項](../ide/feedback-options.md)
* [報告 Mac 視覺工作室的問題](/visualstudio/mac/report-a-problem)
* [回報 C++ 的問題](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [視覺工作室開發人員社區](https://developercommunity.visualstudio.com/)
* [開發人員社群資料隱私權](developer-community-privacy.md)
