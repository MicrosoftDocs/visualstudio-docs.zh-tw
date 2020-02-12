---
title: 在偵錯工具時反編譯 .NET 程式碼 |Microsoft Docs
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 5087c439533aa447708d0f1bfae653054fd16089
ms.sourcegitcommit: a86ee68e3ec23869b6eaaf6c6b7946b1d9a88d01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77144778"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>在進行偵錯工具時，從 .NET 元件產生原始程式碼

在檢查 .NET 應用程式時，您可能會發現您想要查看您沒有的原始程式碼。 例如，在發生例外狀況時中斷，或使用呼叫堆疊來流覽至來源位置。

> [!NOTE]
> * 原始程式碼產生（decompilation）僅適用于 .NET 應用程式，而且是以開放原始碼[ILSpy](https://github.com/icsharpcode/ILSpy)專案為基礎。
> * Decompilation 僅適用于 Visual Studio 2019 16.5 和更新版本。

## <a name="generate-source-code"></a>產生原始程式碼

當您正在進行偵錯工具，但沒有可用的原始程式碼時，Visual Studio 顯示 [找**不到原始**碼] 檔，或如果您沒有元件的符號，則**不會載入任何符號**檔。 這兩個檔都有一個**反編譯**的C#原始程式碼選項，會產生目前位置的程式碼。 產生C#的程式碼就可以像任何其他原始程式碼一樣使用。 您可以查看程式碼、檢查變數、設定中斷點等等。

### <a name="no-symbols-loaded"></a>未載入任何符號

下圖顯示 [**未載入符號**] 訊息。

![未載入符號檔的螢幕擷取畫面](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>找不到來源

下圖顯示 [**找不到來源**] 訊息。

![找不到來原始檔案的螢幕擷取畫面](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>產生並內嵌元件的來源

除了產生特定位置的原始程式碼之外，您還可以產生指定之 .NET 元件的所有原始程式碼。 若要這麼做，請移至 [**模組**] 視窗，並從 .net 元件的內容功能表中，選取 [**反編譯原始程式碼**] 命令。 Visual Studio 會產生元件的符號檔，然後將來源內嵌到符號檔中。 在稍後的步驟中，您可以將內嵌的原始程式碼[解壓縮](#extract-and-view-the-embedded-source-code)。

![[模組] 視窗中具有反編譯來源命令之元件內容功能表的螢幕擷取畫面。](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>將內嵌的原始程式碼解壓縮並加以查看

您可以使用 [**模組**] 視窗的內容功能表中的 [**解壓縮原始程式碼**] 命令，將內嵌在符號檔中的原始程式檔解壓縮。

![[模組] 視窗中具有 [解壓縮來源] 命令之元件內容功能表的螢幕擷取畫面。](media/decompilation-extract-source-code.png)

已解壓縮的來源檔案會以[其他](../ide/reference/miscellaneous-files.md)檔案的形式加入至方案中。 [其他檔案] 功能預設會在 Visual Studio 中關閉。 您可以從 **工具** > **選項**  > **環境** ** > ** 檔 中啟用此功能， > 在方案總管 核取方塊**中顯示其他**檔案 若未啟用這項功能，您將無法開啟已解壓縮的原始程式碼。

![啟用 [其他檔案] 選項之 [工具選項] 頁面的螢幕擷取畫面。](media/decompilation-tools-options-misc-files.png)

已解壓縮的來源檔案會出現在**方案總管**的其他檔案中。

![具有其他檔案的方案瀏覽器螢幕擷取畫面。](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>已知的限制

### <a name="requires-break-mode"></a>需要中斷模式

只有在偵錯工具處於中斷模式且應用程式已暫停時，才可以使用 decompilation 產生原始程式碼。 例如，Visual Studio 在達到中斷點或例外狀況時進入中斷模式。 您可以使用 [**全部中斷**] 命令（![中斷所有圖示](media/decompilation-break-all.png)），輕鬆地觸發下一次執行程式碼時中斷的 Visual Studio。

### <a name="decompilation-limitations"></a>Decompilation 限制

從 .NET 元件中使用的中繼格式（IL）產生原始程式碼有一些固有的限制。 因此，產生的原始程式碼看起來不像原始的原始程式碼。 大部分的差異都是在執行時間不需要原始原始程式碼中資訊的地方。 例如，在執行時間不需要空白字元、批註和區域變數名稱等資訊。 建議您使用產生的來源來瞭解程式的執行方式，而不是原始原始程式碼的取代。

### <a name="debug-optimized-or-release-assemblies"></a>Debug 優化或發行元件

當您從使用編譯器優化編譯的元件進行反向組譯的程式碼時，可能會遇到下列問題：
- 中斷點不一定會系結至相符的來源位置。
- 逐步執行可能不一定會逐步執行至正確的位置。
- 本機變數的名稱不能正確。
- 某些變數可能無法供評估。

如需更多詳細資料，請參閱 GitHub 問題： [IChsarpCompiler. 解編程式整合至 VS 偵錯工具](https://github.com/icsharpcode/ILSpy/issues/1901)。

### <a name="decompilation-reliability"></a>Decompilation 可靠性

相對較小的 decompilation 嘗試百分比可能會導致失敗。 這是因為 ILSpy 中的序列點 null 參考錯誤。  我們已藉由攔截這些問題並正常地將 decompilation 嘗試失敗，以減輕失敗。

如需更多詳細資料，請參閱 GitHub 問題： [IChsarpCompiler. 解編程式整合至 VS 偵錯工具](https://github.com/icsharpcode/ILSpy/issues/1901)。

### <a name="limitations-with-async-code"></a>非同步程式碼的限制

具有 async/await 程式碼模式之反向組譯模組的結果可能不完整或完全失敗。 非同步/等候和產生狀態機器的 ILSpy 實作為僅部分實行。 

如需更多詳細資料，請參閱 GitHub 問題： PDB 產生器[狀態](https://github.com/icsharpcode/ILSpy/issues/1422)。

### <a name="just-my-code"></a>Just My Code

[Just My Code （JMC）](https://docs.microsoft.com/visualstudio/debugger/just-my-code)設定可讓 Visual Studio 逐步執行系統、架構、程式庫和其他非使用者呼叫。 在偵測會話期間，[**模組**] 視窗會顯示偵錯工具視為 My Code （使用者程式碼）所使用的程式碼模組。

優化或發行模組的 Decompilation 會產生非使用者程式碼。 例如，如果偵錯工具在您反向組譯的非使用者程式碼中中斷，則不會顯示 [**任何來源**] 視窗。 若要停用 Just My Code，請流覽至 [**工具**] [ > **選項**] （或 **[** **Debug** > **選項**] **） > debug** > General，然後取消選取 [**啟用 Just My Code**]。

### <a name="extracted-sources"></a>已解壓縮的來源

從元件解壓縮的原始程式碼具有下列限制：
- 無法設定所產生檔案的名稱和位置。
- 這些檔案是暫時性的，而且會被 Visual Studio 刪除。
- 檔案會放在單一資料夾，以及原始來源未使用的任何資料夾階層中。
- 每個檔案的檔案名都包含檔案的總和檢查碼雜湊。

### <a name="generated-code-is-c-only"></a>產生的程式C#代碼僅限
Decompilation 只會在中C#產生原始程式碼檔。 沒有任何其他語言可產生檔案的選項。