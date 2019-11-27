---
title: 如何增加修正效能問題的機率
description: 在 Visual Studio 中提交效能問題的其他資訊和最佳作法
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: d61e7f47fde06c12b6b133ced76e5a8d72d220b0
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74528431"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>如何增加修正效能問題的機率

「回報[問題](https://aka.ms/vs-rap)」工具廣泛由 Visual Studio 使用者用來報告問題的範圍。 Visual Studio 小組會在使用者意見反應中遇到損毀並緩慢趨勢，並解決影響廣泛使用者 swath 的問題。 特定的意見反應票證越容易採取動作，產品小組就越可能很快就能診斷並解決問題。 本檔說明報告當機或緩慢問題時的最佳作法，使其更容易採取動作。

## <a name="general-best-practices"></a>一般最佳作法

Visual Studio 是一個大型、複雜的平臺，支援多種語言、專案類型、平臺等等。 其執行方式是在會話中安裝和使用元件的功能、安裝的延伸模組、Visual Studio 設定、電腦設定，最後是正在編輯之程式碼的圖形。 由於變數數目的不同，因此很難判斷來自某個使用者的問題報告是否與另一位使用者的問題報告具有相同的基礎問題，即使可見的徵兆相同也一樣。 因此，以下是一些最佳作法，可確保您的特定問題報告具有更高的診斷可能性。

**盡可能提供特定的標題**

尋找所回報問題的相異簽章，並盡可能在標題中包含。 如果標題是描述性的，較不可能發生不相關問題的使用者（但相同的表面徵兆）將會對您的票證進行投票或留言，因此更難診斷*您*的問題。

**若不確定，請記錄新的問題報告**

許多問題可能不會有任何特殊的簽章或重現的步驟。 在這種情況下，新的報表會比附議或另一份報表上的批註更好，這會報告類似的外部*徵兆*。 視報表的類型而定，將其他診斷檔案包含在您的報表中，如本檔稍後所述。

**問題特有的最佳作法**

以下描述的問題很難診斷，而不需要有良好的診斷檔案。 找出最能描述您問題的案例之後，請遵循該案例的特定意見反應步驟。

-   當機[：](#crashes)當進程（Visual Studio）意外終止時，就會發生損毀。

-   [無回應：](#unresponsiveness)VS 會變得沒有回應一段頗長的時間。

-   [緩慢問題：](#slowness-and-high-cpu-issues)VS 中的任何特定動作速度低於所需

-   [高 CPU：](#slowness-and-high-cpu-issues)非預期的高 CPU 使用量長時間

## <a name="crashes"></a>發生
當進程（Visual Studio）意外終止時，就會發生損毀。

**直接重現損毀**

直接可重現的損毀是具有下列所有特性的案例：

- 可以遵循一組已知的步驟來觀察

- 可以在多部電腦上觀察到（如果有的話）

- 可以在範例程式碼中重現，或在可連結或提供作為意見反應一部分的專案中重新產生（如果步驟牽涉到開啟專案或檔）

針對這些問題，請遵循「如何回報[問題](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)」中的步驟，並務必包含：

-   重現問題的步驟

-   如上面所述的獨立重現專案。 如果不可能進行獨立重現，請包含：

    -   開啟專案的語言（C\#、 C++等）

    -   專案類型（主控台應用程式、ASP.NET 等）


> [!NOTE]
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是重現問題的一組步驟和範例原始程式碼。

**不明的當機**

如果您不確定造成當機或其為隨機的原因，您可以在每次 Visual Studio 損毀時，于本機捕捉傾印，並將其附加至個別的意見專案。 若要在 Visual Studio 損毀時將傾印儲存在本機，請在 [系統管理員命令] 視窗中執行下列命令：

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

適當地自訂傾印計數和傾印資料夾。 如需這些設定的詳細資訊，請參閱[這裡](https://docs.microsoft.com/windows/win32/wer/collecting-user-mode-dumps?redirectedfrom=MSDN)。

> [!NOTE]
> 使用工作管理員所捕捉到的傾印可能是錯誤的位，因此較不能使用。 前述程式是捕捉堆積傾印的慣用方式。 如果您想要使用 [工作管理員]，請關閉目前正在執行的工作管理員，啟動32位工作管理員（% windir%\\syswow64\\taskmgr），並從該處收集堆積傾印。

> [!NOTE] 
> 此方法所產生的每個傾印檔案，大小上限為 4 GB。 請務必將 DumpFolder 設定為具有足夠磁碟空間的位置，或適當地調整 DumpCount。

每次 Visual Studio 損毀時，它會建立一個傾印檔（ **devenv .exe）。 [number] dmp**檔案已設定的位置。

然後，使用 Visual Studio 的「回報問題 ...」特徵. 它可讓您附加適當的傾印。

1.  找出您所報告之損毀的傾印檔案（尋找具有正確建立時間的檔案）

2.  可能的話，請在提交意見反應之前壓縮檔案（\*.zip）以縮小其大小

3.  遵循「[如何回報問題](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)」中的步驟，並將堆積傾印附加至新的意見反應專案。

> [!NOTE] 
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是在當機時所捕捉到的堆積傾印。

## <a name="unresponsiveness"></a>無回應
VS 會變得沒有回應一段頗長的時間。

**直接重現無回應**

如發生損毀的對應章節中所述，對於可輕易重現的問題，在多部電腦上看得到，而且可以在小型範例中示範，最寶貴的意見報告包括重現問題的步驟，並包含示範問題的原始碼範例。

**未知的無回應**

如果無回應以無法預期的方式來進行資訊清單，在下一次出現時，啟動 Visual Studio 的新實例，並從該實例回報問題。
在 [[記錄] 畫面](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)中，請務必選取已停止回應的 Visual Studio 會話。

如果在系統管理員模式中啟動了無回應的 Visual Studio 實例，則第二個實例也必須以系統管理員模式啟動。

>[!NOTE] 
> **最寶貴的意見反應：** 在此情況下，最寶貴的意見反應是在無回應時所捕捉到的堆積傾印。

## <a name="slowness-and-high-cpu-issues"></a>緩慢和高 CPU 問題

當緩慢的作業或高 CPU 事件正在進行時，所捕捉到的效能追蹤會導致緩慢或高 CPU 使用量問題最具動作。

>[!NOTE] 
> 可能的話，請將每個案例隔離在個別的特定意見反應報告中。
例如，如果輸入和流覽速度都很慢，請針對每個問題遵循下列步驟一次。 這可協助產品小組找出特定問題的原因。

若要獲得最佳效能，請遵循下列步驟：

1.  如果尚未執行，請複製 Visual Studio 開啟，您將會在其中重現問題

    -   已設定所有專案來重現問題。 例如，如果您需要在開啟特定檔案時載入特定專案，請確定這兩個步驟都已完成，然後再繼續進行。

    -   如果您*未*回報載入解決方案的特定問題，請在錄製效能追蹤之前，嘗試等候5-10 分鐘（或更多，視解決方案大小而定）。 解決方案載入程式會產生大量的資料，因此等候幾分鐘的時間，可協助我們將焦點放在您所報告的特定問題。

2.  啟動 Visual Studio 的第二個複本 *，而不開啟任何解決方案*

3.  在 Visual Studio 的新複本中，開啟 [回報**問題**] 工具

4.  請遵循如何回報[問題](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)中的步驟，直到您到達「提供追蹤和堆積傾印（選擇性）」步驟為止。

5.  選擇記錄 Visual Studio 的第一份複本（遇到效能問題的人）並開始錄製。

    -   隨即會出現 [錄製器] 應用程式，並開始錄製。

    -   在**錄製期間，請**在 Visual Studio 的第一個複本中執行有問題的動作。 如果沒有出現在記錄的時間內，我們很難以修正特定的效能問題。

    -   如果動作短于30秒，而且可以輕鬆地重複，請重複此動作以進一步示範問題。

    -   在大部分情況下，60秒的追蹤就足以示範問題，特別是有問題的動作持續（或重複）超過30秒時。 您可以視需要調整持續時間，以捕捉您想要修正的行為。

6.  當您想要報告的緩慢作業或高 CPU 事件完成時，請在步驟錄製器中按一下 [停止錄製]。 可能需要幾分鐘的時間來處理效能追蹤。

7.  完成後，將會有數個附件可供您的意見反應。 附加可能有助於重現問題的任何其他檔案（範例專案、螢幕擷取畫面、影片等等）。

8.  提交意見反應。

在錄製效能追蹤時，如果您要回報的緩慢作業或高 CPU 已到達結尾，則會立即停止錄製。 如果收集的資訊太多，則會覆寫最舊的資訊。 如果在有趣的作業之後，追蹤並未立即停止（在幾秒內），則會覆寫有用的追蹤資料。

請勿直接將效能追蹤附加至開發人員論壇網站上的現有意見反應專案。 Visual Studio 內建的「回報問題」工具中，要求/提供其他資訊是支援的工作流程。 如果需要效能追蹤才能解決先前的意見專案，我們會將意見反應專案的狀態設定為「需要更多資訊」，這可以用與報告新問題的相同方式回應。 如需詳細指示，請參閱報告問題工具的檔中的「[需要更多資訊」一節](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info)。

> [!NOTE] 
> **最寶貴的意見反應：** 對於幾乎所有的緩慢/高 CPU 問題，最寶貴的意見反應是您嘗試執行之動作的高階描述，以及效能追蹤（\*.etl），它會在這段時間內捕捉行為。

**先進的效能追蹤**

在「報告-問題」工具中的追蹤收集功能，足以應付大部分的情況。 但有時候需要更多的追蹤收集控制權（例如，具有較大緩衝區大小的追蹤），在此情況下，PerfView 是很棒的工具可供使用。 使用 PerfView 工具手動錄製效能追蹤的步驟，請參閱使用[PerfView 記錄效能](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)追蹤頁面。

## <a name="see-also"></a>請參閱

* [Visual Studio 意見反應選項](../ide/feedback-options.md)
* [回報 Visual Studio for Mac 的問題](/visualstudio/mac/report-a-problem)
* [回報 C++ 的問題](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)
* [Developer Community 資料隱私權](developer-community-privacy.md)
