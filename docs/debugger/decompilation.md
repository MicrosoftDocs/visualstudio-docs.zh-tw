---
title: 在偵錯工具時，將 .NET 程式碼進行編譯 |Microsoft Docs
description: 在 Visual Studio 中進行偵錯工具時，從 .NET 元件產生和內嵌原始程式碼。 解壓縮並查看內嵌的原始程式碼。
ms.custom: SEO-VS-2020
ms.date: 2/2/2020
ms.topic: how-to
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
ms.openlocfilehash: 8ad919b14642dff98746c194ad8c05bbb3aea529
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726731"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>在偵錯工具時，從 .NET 元件產生原始程式碼

在對 .NET 應用程式進行偵錯工具時，您可能會發現您想要查看您沒有的原始程式碼。 例如，中斷例外狀況，或使用呼叫堆疊流覽至來源位置。

> [!NOTE]
> * 原始程式碼產生 (反向組譯) 僅適用于 .NET 應用程式，並以開放原始碼 [ILSpy](https://github.com/icsharpcode/ILSpy) 專案為基礎。
> * 反向組譯僅適用于 Visual Studio 2019 16.5 和更新版本。
> * 將 [SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) 屬性套用至元件或模組，可防止 Visual Studio 嘗試反向組譯。

## <a name="generate-source-code"></a>產生原始程式碼

當您正在進行偵錯工具且沒有原始程式碼可用時，Visual Studio 會顯示 [ **找不到來源** ] 檔，或如果您沒有元件的符號，則 **不會載入符號** 檔。 這兩份檔都有一個可針對目前位置產生 c # 程式碼的 **反編碼原始程式碼** 選項。 然後可以使用產生的 c # 程式碼，就像任何其他原始程式碼一樣。 您可以查看程式碼、檢查變數、設定中斷點等等。

### <a name="no-symbols-loaded"></a>未載入任何符號

下圖顯示 **未載入符號** 的訊息。

![未載入符號的檔螢幕擷取畫面](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>找不到來源

下圖顯示「 **找不到來源** 」訊息。

![找不到來原始檔案的螢幕擷取畫面](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>產生和內嵌元件的來源

除了產生特定位置的原始程式碼之外，您還可以產生指定之 .NET 元件的所有原始程式碼。 若要這樣做，請移至 [ **模組** ] 視窗，然後從 .net 元件的內容功能表中，選取 [反組解碼 **原始程式碼** ] 命令。 Visual Studio 會產生元件的符號檔，然後將來源內嵌至符號檔。 在稍後的步驟中，您可以 [解壓縮](#extract-and-view-the-embedded-source-code) 內嵌的原始程式碼。

![[模組] 視窗中具有反組解碼來源命令的元件內容功能表螢幕擷取畫面。](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>解壓縮和查看內嵌的原始程式碼

您可以使用 [**模組**] 視窗的操作功能表中的 [**解壓縮原始程式碼**] 命令，將內嵌在符號檔中的原始程式檔解壓縮。

![[模組] 視窗中具有 [解壓縮來源] 命令的元件內容功能表螢幕擷取畫面。](media/decompilation-extract-source-code.png)

已解壓縮的來源檔案會以 [其他](../ide/reference/miscellaneous-files.md)檔案的形式加入至方案。 在 Visual Studio 中，[其他檔案] 功能預設為關閉。 您可以從 [**工具**  >  **選項**  >  **環境**  >  **檔**  >  **在方案總管中顯示其他** 檔案] 核取方塊啟用這項功能。 若未啟用此功能，您將無法開啟已解壓縮的原始程式碼。

![啟用 [其他檔案] 選項之 [工具選項] 頁面的螢幕擷取畫面。](media/decompilation-tools-options-misc-files.png)

解壓縮的原始檔會出現在 **方案總管** 的其他檔案中。

![包含其他檔案的方案瀏覽器螢幕擷取畫面。](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>已知限制

### <a name="requires-break-mode"></a>需要中斷模式

只有當偵錯工具處於中斷模式且應用程式已暫停時，才可以使用反向組譯產生原始程式碼。 例如，Visual Studio 在達到中斷點或例外狀況時進入中斷模式。 您可以使用 [ **全部中斷** ] 命令，輕鬆地觸發 Visual Studio，以便在下一次執行程式碼時中斷 (![ 全部中斷圖示 ](media/decompilation-break-all.png)) 。

### <a name="decompilation-limitations"></a>反向組譯限制

從中繼格式產生原始程式碼 (在 .NET 元件中使用的 IL) 會有一些固有的限制。 因此，產生的原始程式碼看起來不像原始原始程式碼。 大部分的差異是在執行時間不需要原始原始程式碼中資訊的位置。 例如，在執行時間不需要空白字元、批註和區域變數的名稱等資訊。 建議您使用產生的來源，以瞭解程式的執行方式，而不是原始原始程式碼的取代專案。

### <a name="debug-optimized-or-release-assemblies"></a>偵錯工具優化或發行元件

當您從使用編譯器優化編譯的元件反向組譯錯程式碼時，可能會遇到下列問題：
- 中斷點可能不一定會系結至相符的來源位置。
- 逐步執行不一定會逐步執行至正確的位置。
- 本機變數的名稱可能不正確。
- 某些變數可能無法用於評估。

如需更多詳細資料，請參閱 GitHub 問題： [ICSharpCode. 解編程式與 VS 偵錯工具的整合](https://github.com/icsharpcode/ILSpy/issues/1901)。

### <a name="decompilation-reliability"></a>反向組譯可靠性

相對較少的反向組譯嘗試百分比可能會導致失敗。 這是因為 ILSpy 中的序列點 null 參考錯誤所致。  我們藉由攔截這些問題並正常地失敗反向組譯嘗試，來減輕失敗。

如需更多詳細資料，請參閱 GitHub 問題： [ICSharpCode. 解編程式與 VS 偵錯工具的整合](https://github.com/icsharpcode/ILSpy/issues/1901)。

### <a name="limitations-with-async-code"></a>非同步程式碼的限制

具有 async/await 程式碼模式之反向組譯模組的結果可能不完整或整個失敗。 Async/await 和 yield 狀態的 ILSpy 執行僅部分實行。 

您可以在 GitHub 問題： PDB 產生器 [狀態](https://github.com/icsharpcode/ILSpy/issues/1422)中找到更多詳細資料。

### <a name="just-my-code"></a>Just My Code

[Just My Code (JMC) ](./just-my-code.md)設定可讓 Visual Studio 不進入系統、架構、程式庫及其他非使用者呼叫。 在偵錯工具中，[ **模組** ] 視窗會顯示偵錯工具視為 My Code (使用者程式碼) 的程式碼模組。

優化或發行模組的反向組譯會產生非使用者程式碼。 例如，如果偵錯工具在您反向組譯的非使用者程式碼中中斷，則不會出現 **任何來源** 視窗。 若要停用 Just My Code，請流覽至 [**工具**  >  **選項**] (或 [**調試**  >  **選項**]) >   >  **[一般**]，然後取消選取 [**啟用 Just My Code**]。

### <a name="extracted-sources"></a>已解壓縮來源

從元件解壓縮的原始程式碼具有下列限制：
- 無法設定所產生檔案的名稱和位置。
- 這些檔案是暫時性的，而且將會 Visual Studio 刪除。
- 這些檔案會放在單一資料夾中，而且不會使用原始來源的任何資料夾階層。
- 每個檔案的檔案名都包含檔案的總和檢查碼雜湊。

### <a name="generated-code-is-c-only"></a>產生的程式碼僅限 c #
反向組譯只會在 c # 中產生原始程式碼檔。 沒有任何其他語言可以產生檔案的選項。