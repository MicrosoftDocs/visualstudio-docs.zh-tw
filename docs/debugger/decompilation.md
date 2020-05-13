---
title: 調試時解編譯 .NET 代碼 |微軟文檔
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
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508741"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>調試時從 .NET 程式集生成原始程式碼

調試 .NET 應用程式時，您可能會發現要查看沒有的原始程式碼。 例如，打破異常或使用呼叫堆疊導航到源位置。

> [!NOTE]
> * 原始程式碼生成（解編譯）僅適用于 .NET 應用程式，並且基於開源[ILSpy](https://github.com/icsharpcode/ILSpy)專案。
> * 解編譯僅在 Visual Studio 2019 16.5 及更高版本中提供。
> * 將["禁止 Ildasm 屬性"屬性](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute)應用於程式集或模組可防止 Visual Studio 嘗試取消編譯。

## <a name="generate-source-code"></a>生成原始程式碼

當您正在調試且沒有原始程式碼可用時，Visual Studio 將顯示 **"源未找到"** 文檔，或者如果沒有程式集的符號"**已載入無符號"** 文檔。 這兩個文檔都有一個 **"去編譯"原始程式碼**選項，用於生成當前位置的 C# 代碼。 然後，可以使用生成的 C# 代碼，就像使用任何其他原始程式碼一樣。 您可以查看代碼、檢查變數、設置中斷點等。

### <a name="no-symbols-loaded"></a>未載入符號

下圖顯示了 **"無符號載入"** 消息。

![無符號載入文檔的螢幕截圖](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>未找到源

下圖顯示了 **"未找到源"** 消息。

![未找到來源文件的螢幕截圖](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>生成和嵌入程式集的源

除了為特定位置生成原始程式碼外，還可以為給定的 .NET 程式集生成所有原始程式碼。 為此，請轉到**模組**視窗和 .NET 程式集的內容功能表，然後選擇 **"去編譯原始程式碼**"命令。 Visual Studio 為程式集生成符號檔，然後將源嵌入到符號檔中。 在後面的步驟中，可以[提取](#extract-and-view-the-embedded-source-code)嵌入的原始程式碼。

![具有取消編譯源命令的模組視窗中程式集內容功能表的螢幕截圖。](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>提取和查看嵌入的原始程式碼

您可以使用 **"模組"** 視窗的內容功能表中的 **"提取原始程式碼"** 命令提取嵌入在符號檔中的原始檔案。

![具有資料提取源命令的模組視窗中程式集內容功能表的螢幕截圖。](media/decompilation-extract-source-code.png)

提取的原始檔案將作為[雜項檔](../ide/reference/miscellaneous-files.md)添加到解決方案中。 預設情況下，在 Visual Studio 中，雜項檔功能處於關閉狀態。 您可以在 **"工具** > **選項** > **環境** > **Documents**文檔 > **在解決方案資源管理器"核取方塊中顯示"雜項檔**"中啟用此功能。 如果不啟用此功能，您將無法打開提取的原始程式碼。

![啟用了"雜項檔"選項的工具選項頁的螢幕截圖。](media/decompilation-tools-options-misc-files.png)

提取的原始檔案將顯示在**解決方案資源管理器**中的雜項檔中。

![包含雜項檔的解決方案資源管理器的螢幕截圖。](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>已知限制

### <a name="requires-break-mode"></a>需要中斷模式

僅當調試器處於中斷模式且應用程式暫停時，才可能使用解編譯生成原始程式碼。 例如，Visual Studio 在達到中斷點或異常時進入中斷模式。 您可以使用"**全部中斷"** 命令（斷開所有圖示![](media/decompilation-break-all.png)）輕鬆觸發 Visual Studio 以在下次運行代碼時中斷代碼。

### <a name="decompilation-limitations"></a>取消編譯限制

從 .NET 程式集中使用的中間格式 （IL） 生成原始程式碼有一些固有的限制。 因此，生成的原始程式碼看起來不像原始原始程式碼。 大多數差異是在運行時不需要原始原始程式碼中的資訊的地方。 例如，運行時不需要空格、注釋和區域變數的名稱等資訊。 我們建議您使用生成的源來瞭解程式的執行方式，而不是作為原始原始程式碼的替換。

### <a name="debug-optimized-or-release-assemblies"></a>調試優化或釋放程式集

調試從使用編譯器優化編譯的程式集中解編譯的代碼時，可能會遇到以下問題：
- 中斷點可能並不總是綁定到匹配的採購位置。
- 步進可能並不總是步進到正確的位置。
- 區域變數可能沒有準確的名稱。
- 某些變數可能可用於評估。

更多詳細資訊請參閱 GitHub 問題[：ICSharpCode.De編譯器集成到 VS 調試器](https://github.com/icsharpcode/ILSpy/issues/1901)中。

### <a name="decompilation-reliability"></a>取消編譯可靠性

相對較少的取消編譯嘗試可能會導致失敗。 這是由於 ILSpy 中的序列點 null 引用錯誤。  我們通過抓住這些問題並優雅地失敗刪除編譯嘗試來減輕失敗。

更多詳細資訊請參閱 GitHub 問題[：ICSharpCode.De編譯器集成到 VS 調試器](https://github.com/icsharpcode/ILSpy/issues/1901)中。

### <a name="limitations-with-async-code"></a>不同步代碼的限制

使用非同步/等待代碼模式取消編譯模組的結果可能不完整或完全失敗。 只部分實現了非同步/await 和屈服狀態機的 ILSpy 實現。 

更多詳細資訊可在 GitHub 問題中找到[：PDB 產生器狀態](https://github.com/icsharpcode/ILSpy/issues/1422)。

### <a name="just-my-code"></a>Just My Code

["僅我的代碼 （JMC）"](https://docs.microsoft.com/visualstudio/debugger/just-my-code)設置允許 Visual Studio 跨跨系統、框架、庫和其他非使用者呼叫。 在調試會話期間，"**模組"** 視窗顯示調試器將哪些代碼模組視為"我的代碼"（使用者代碼）。

取消編譯優化或發佈模組會產生非使用者代碼。 例如，如果調試器在已編譯的非使用者代碼中中斷，則會出現 **"無源"** 視窗。 要禁用"僅我的代碼"，請導航到 **"工具** > **選項**"（或**調試** > **選項**）>**調試** > **常規**，然後取消選擇**僅啟用我的代碼**。

### <a name="extracted-sources"></a>提取的源

從程式集中提取的原始程式碼具有以下限制：
- 生成的檔的名稱和位置不可配置。
- 這些檔是臨時的，將由 Visual Studio 刪除。
- 這些檔放置在單個資料夾中，並且不使用原始源的任何資料夾層次結構。
- 每個檔的檔案名包含檔的校驗和雜湊。

### <a name="generated-code-is-c-only"></a>生成的代碼僅為 C#
解編譯僅在 C# 中生成原始程式碼檔。 沒有以任何其他語言生成檔的選項。
