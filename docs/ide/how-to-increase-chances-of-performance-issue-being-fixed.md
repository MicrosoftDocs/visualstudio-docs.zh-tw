---
title: 增加修正效能問題的機會
description: 在 Visual Studio 中提交效能問題的其他資訊和最佳作法
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jmartens
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: d3db409c67ab961adfceaeb8e3236cd964f95399
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962895"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>如何提高修正效能問題的機會

Visual Studio 使用者廣泛使用「回報[問題](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true)」工具來回報各種問題。 Visual Studio 團隊會在使用者意見反應中損毀並緩慢趨勢，並解決影響廣泛使用者 swath 的問題。 特定意見反應票證越可採取動作，產品團隊越可能更容易診斷及解決。 本檔說明報告損毀或緩慢問題時的最佳作法，使其更具可採取動作。

## <a name="general-best-practices"></a>一般最佳作法

Visual Studio 是一種大型、複雜的平臺，可支援多種語言、專案類型、平臺等等。 其執行方式是在會話中安裝和使用中的元件、已安裝的擴充功能、Visual Studio 設定、電腦設定，最後是正在編輯之程式碼的圖形。 由於變數數目的不同，因此很難分辨來自某位使用者的問題報告是否與另一位使用者的問題報告具有相同的根本問題，即使可見的徵兆相同也是一樣。 因此，以下是一些最佳作法，以確保您的特定問題報告有更高的診斷可能性。

**盡可能提供特定的標題**

尋找所回報問題的相異簽章，並盡可能將其包含在標題中。 如果標題是描述性的，則較不可能有不相關問題的使用者 (但表面徵兆) 會對您的票證投票或留言，進而讓 *您* 的問題診斷變得更困難。

**如果不確定，請記錄新的問題報告**

許多問題可能沒有任何特殊的簽章或要重現的步驟。 在這種情況下，新的報表比附議或在另一份報表上的評論更好，這會報告類似的外接 *徵兆*。 根據報表的類型，將其他診斷檔案包含在您的報表中，如本檔稍後所述。

**特定問題的最佳作法**

以下描述的問題很難診斷而沒有良好的診斷檔案。 找出最能描述問題的案例之後，請遵循該案例的特定意見反應步驟。

- 當機[：](#crashes)當進程 (Visual Studio) 意外終止時，就會發生損毀。

- [無回應：](#unresponsiveness) VS 會有一段很長的時間沒有回應。

- [緩慢問題：](#slowness-and-high-cpu-issues) VS 中的任何特定動作都比所需的還要慢

- [高 CPU：](#slowness-and-high-cpu-issues) 非預期的高 CPU 使用率期間延長

- [跨進程問題：](#out-of-process-issues) Visual Studio 附屬進程所造成的問題

## <a name="crashes"></a>損毀
當進程 (Visual Studio) 意外終止時，就會發生損毀。

**直接可重現的損毀**

直接可重現的損毀是具有下列所有特性的案例：

- 可以遵循一組已知的步驟來觀察

- 可以在多部電腦上觀察 (如有提供) 

- 如果步驟牽涉到開啟專案或) 檔，可以在範例程式碼或可連結至或提供作為意見反應一部分的專案中重現 (

針對這些問題，請遵循「如何回報[問題](./how-to-report-a-problem-with-visual-studio.md)」中的步驟，並務必包含：

- 重現問題的步驟

- 如上所述的獨立重現專案。 如果不可能進行獨立重現，請包含：

  - 開啟專案的語言 (C \# 、c + + 等 ) 

  - 專案 (主控台應用程式、ASP.NET 等的種類 ) 

> [!NOTE]
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是一組重現問題的步驟，以及範例原始程式碼。

**未知的損毀**

如果您不確定造成當機或其看似隨機的原因，您可以在每次 Visual Studio 損毀時于本機捕獲傾印，並將其附加至個別的意見專案。 當 Visual Studio 損毀時，若要在本機儲存傾印，請在系統管理員命令視窗中執行下列命令：

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

視需要自訂傾印計數和傾印資料夾。 請在 [這裡](/windows/win32/wer/collecting-user-mode-dumps)找到這些設定的詳細資訊。

> [!NOTE]
> 使用工作管理員所捕捉的傾印可能是錯誤的位，因此不能使用。 上述程式是捕獲堆積傾印的慣用方法。 如果您想要使用工作管理員，請關閉目前正在執行的帳戶，啟動32位工作管理員 (% windir% \\ syswow64 \\taskmgr.exe) ，然後從該處收集堆積傾印。

> [!NOTE]
> 這個方法所產生的每個傾印檔案大小上限為 4 GB。 請務必將 DumpFolder 設定為具有適當磁片磁碟機空間的位置，或適當地調整 DumpCount。

每次 Visual Studio 損毀時，就會devenv.exe 建立傾印檔案 **。number]** 在設定的位置中的 dmp 檔案。

然後，使用 Visual Studio 的「回報問題 ...」特徵。 它可讓您附加適當的傾印。

1. 找出您要報告的損毀傾印檔案 (尋找具有正確建立時間的檔案) 

2. 可能的話，請將檔案壓縮 (\* .zip) ，以在提交意見反應之前縮減其大小

3. 遵循「[如何報告問題](./how-to-report-a-problem-with-visual-studio.md)」中的步驟，並將堆積傾印附加至新的意見專案。

> [!NOTE]
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是在損毀時捕捉的堆積傾印。

## <a name="unresponsiveness"></a>無回應
VS 會有一段很長的時間沒有回應。

**直接可重現的無回應**

如在發生損毀的對應章節中所述，對於可以輕鬆重現的問題，在多部電腦上看得到，而且可以在小型範例中示範，最寶貴的意見報告是包含重現問題的步驟，並包含示範問題的範例原始程式碼。

**未知的無回應**

如果無回應以無法預期的方式資訊清單，在下一次出現時，會啟動 Visual Studio 的新實例，並從該實例回報問題。
在 [記錄] 畫面中，請務必選取沒有回應的 Visual Studio 會話。  (如需如何記錄可追蹤以重現問題之動作的詳細資訊，請參閱 [如何回報問題](./how-to-report-a-problem-with-visual-studio.md) 頁面上的步驟8。 ) 

如果沒有回應的 Visual Studio 實例是以系統管理員模式啟動，則第二個實例也需要在系統管理員模式下啟動。

>[!NOTE]
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是在無回應時所捕捉的堆積傾印。

## <a name="slowness-and-high-cpu-issues"></a>緩慢和高 CPU 問題

造成緩慢或高 CPU 使用量問題的最高動作，就是當執行緩慢作業或高 CPU 事件正在進行時所捕捉到的效能追蹤。

>[!NOTE]
> 可能的話，請將每個案例隔離在個別的特定意見報告中。
例如，如果輸入和流覽都很慢，請針對每個問題遵循下列步驟一次。 這可協助產品團隊找出特定問題的原因。

為了獲得最佳的效能，請遵循下列步驟：

1. 如果尚未執行，請在您將重現問題的 Visual Studio 開啟複本

    - 讓所有專案都已設定重現問題。 例如，如果您需要在開啟特定檔案的情況下載入特定專案，則在繼續之前，請確定這兩個步驟都已完成。

    - 如果您 *未* 回報載入解決方案的特定問題，請嘗試等待5-10 分鐘 (或更多，視方案大小) 在記錄效能追蹤之前開啟解決方案之後。 解決方案載入程式會產生大量資料，因此等候幾分鐘的時間，可協助我們專注于您所報告的特定問題。

2. 啟動 Visual Studio 的第二個複本 *，未開啟任何解決方案*

3. 在 Visual Studio 的新複本中，開啟 [回報 **問題** ] 工具

4. 遵循 [如何回報問題](./how-to-report-a-problem-with-visual-studio.md) 的步驟，直到您到達「提供追蹤和堆積傾印 (選擇性) 」步驟。

5. 選擇記錄 Visual Studio 的第一個複本 (發生效能問題) 並開始錄製。

    - [步驟錄製器] 應用程式隨即出現，並開始錄製。

    - 在 **錄製期間，請** 在 Visual Studio 的第一個複本中執行有問題的動作。 如果沒有出現在錄製的時間內，我們很難更正特定效能問題。

    - 如果動作少於30秒，而且可以輕鬆地重複，請重複執行此動作以進一步展示問題。

    - 在大部分的情況下，60秒的追蹤就足以展示問題，特別是如果有問題的動作持續 (或重複) 超過30秒。 您可以視需要調整持續時間，以捕捉您要修正的行為。

6. 當您想要報告的緩慢作業或高 CPU 事件完成時，請按一下 [步驟錄製器] 中的 [停止錄製]。 可能需要幾分鐘的時間來處理效能追蹤。

7. 完成之後，您的意見反應將會有數個附件。 附加可能有助於重現問題的任何其他檔案 (範例專案、螢幕擷取畫面、影片等 ) 。

8. 提交意見反應。

在記錄效能追蹤時，如果您要報告的緩慢作業或高 CPU 已結束，則會立即停止錄製。 如果收集太多資訊，則會覆寫最舊的資訊。 如果追蹤未在幾秒鐘內停止 () 在有趣的作業之後，就會覆寫有用的追蹤資料。

請勿直接將效能追蹤附加至開發人員社群網站上的現有意見反應專案。 Visual Studio 的內建「回報問題」工具中，要求/提供其他資訊是支援的工作流程。 如果需要效能追蹤才能解決先前的意見專案，我們會將意見專案的狀態設為「需要更多資訊」，這可透過與報告新問題相同的方式回應。 如需詳細指示，請參閱「回報問題」工具檔中的「 [需要更多資訊」一節](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) 。

> [!NOTE]
> **最寶貴的意見反應：** 對於幾乎所有的緩慢/高 CPU 問題而言，最有價值的意見反應是您嘗試進行之動作的高階描述，以及效能追蹤 (\*.etl.zip) 會在該時間內捕捉行為。

**Advanced Performance 追蹤**

在大部分的案例中，「報表-問題」工具中的追蹤集合功能已足夠。 但有時候需要更充分掌控追蹤收集 (例如，具有較大緩衝區大小的追蹤) ，在此情況下，PerfView 是很棒的工具可供使用。 使用 PerfView 工具手動錄製效能追蹤的步驟，可以在 [ [使用 PerfView 錄製效能](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md) 追蹤] 頁面上找到。

## <a name="out-of-process-issues"></a>跨進程問題

> [!NOTE]
> 從 Visual Studio 2019 16.3 版開始，系統會自動將跨進程記錄檔附加至使用 [回報問題] 工具提交的意見反應。
但是，如果問題是直接重現的，則遵循下列步驟仍然可以協助新增額外資訊，以協助更妥善診斷問題。

有幾個附屬進程會平行執行以 Visual Studio，並從主要 Visual Studio 進程以外提供各種功能。 如果其中一個附屬進程發生錯誤，通常會在 Visual Studio 端看到 ' StreamJsonRpc. RemoteInvocationException ' 或 ' StreamJsonRpc. ConnectionLostException '。

造成這些類型的問題最可行的方式，是提供可透過下列步驟來收集的其他記錄：

1. 如果這是直接可重現的問題，請從刪除 **% temp%/servicehub/logs** 資料夾開始。 如果您無法重現此問題，請將此資料夾保持不變，並忽略下列專案符號：

    - 將全域環境變數 **ServiceHubTraceLevel** 設定為 **All**
    - 重現問題。

2. 在 [這裡](https://www.microsoft.com/download/details.aspx?id=12493)下載 Microsoft Visual Studio 和 .NET Framework 記錄收集工具。
3. 執行工具。 這會將 zip 檔案輸出到 **% temp/vslogs.zip**。 請將該檔案附加到您的意見反應。

## <a name="see-also"></a>另請參閱

* [Visual Studio 意見反應選項](../ide/feedback-options.md)
* [報告 Visual Studio for Mac 的問題](/visualstudio/mac/report-a-problem)
* [回報 C++ 的問題](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)
* [開發人員社群資料隱私權](developer-community-privacy.md)