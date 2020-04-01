---
title: 針對程式碼涵蓋範圍進行疑難排解
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 39d5d54021e7b8286bd653941d233a73bcf8cfb4
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80528001"
---
# <a name="troubleshoot-code-coverage"></a>對程式碼涵蓋範圍進行疑難排解

Visual Studio 中的代碼覆蓋率分析工具收集本機程式集和託管程式集 *(.dll*或 *.exe*檔案)的數據。 但是,在某些情況下,"**代碼覆蓋率結果**「視窗顯示類似於」生成的空結果:..."的錯誤。有幾個原因,為什麼你可以得到空的結果。 本文可協助您解決這些問題。

## <a name="what-you-should-see"></a>您應該會看到

如果在 **「測試」** 選單上選擇 **「分析代碼覆寫率**」命令,並且產生和測試成功運行,則應在 **「代碼覆蓋率」** 視窗中看到結果清單。 您可能必須展開項目才能查看詳細資料。

::: moniker range=">=vs-2019"
![顯示著色內容的程式碼涵蓋範圍結果](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![顯示著色內容的程式碼涵蓋範圍結果](../test/media/codecoverage1.png)
::: moniker-end

如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>看不見任何結果或看見舊結果的可能原因

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>您的 Visual Studio 版本是否正確?

您需具備 Visual Studio 企業版。

### <a name="no-tests-were-executed"></a>沒有執行過任何測試

分析&mdash;請查看輸出視窗。 在 [顯示輸出來源]**** 下拉式清單中選擇 [測試]****。 檢查是否有記錄任何警告或錯誤。

說明&mdash;程式碼涵蓋範圍分析會在執行測試時進行。 這項分析只包括在執行測試時載入記憶體的組件。 如果沒有執行任何測試，程式碼涵蓋範圍就不會產生任何報告。

解決方式&mdash;在 [測試總管] 中，選擇 [全部執行]****，確認所執行的測試是否成功。 在使用 [分析程式碼涵蓋範圍]**** 之前修正所有錯誤。

### <a name="youre-looking-at-a-previous-result"></a>您看到的是之前的結果

當您修改並重新執行測試時，可能仍會顯示先前的程式碼涵蓋範圍結果，包括在先前執行時著色的程式碼。

1. 執行**分析碼覆寫率**。

2. 請確保在 **「代碼覆蓋率結果」** 視窗中選擇了最新的結果集。

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (符號) 檔案無法使用

分析&mdash;打開編譯目標資料夾(通常為*bin_debug),* 並驗證每個程式集中與 *.dll*或 *.exe*檔在同一目錄中有一個 *.pdb*檔。

說明&mdash;代碼覆蓋率引擎要求每個程式集在測試運行期間都有其關聯的 *.pdb*檔案可訪問。 如果特定程式集沒有 *.pdb*檔,則不分析程式集。

*.pdb*文件必須從與 *.dll*或 *.exe*檔案相同的生成生成。

解決方法&mdash;確保生成設置生成 *.pdb*檔。 如果在產生項目時未更新 *.pdb*檔案,則開啟項目屬性,選擇 **「 產生」** 頁,選擇 **「進階**」 並檢查**除錯資訊**。

對於C++專案,請確保生成的 .pdb 檔具有完整的調試資訊。 打開專案屬性並驗證**連結器** > **調試** > **生成調試資訊**設置為**生成優化用於共用和發佈的調試資訊 (/DEBUG:FULL)。**

如果 *.pdb*和 *.dll*或 *.exe*檔案位於不同位置,請將 *.pdb*檔案複製到同一目錄。 還可以配置代碼覆蓋率引擎以在另一個位置搜索 *.pdb*檔。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

### <a name="use-an-instrumented-or-optimized-binary"></a>使用已檢測或最佳化的二進位檔

分析&mdash;確定二進位檔是否經歷了任何形式的高級優化,如配置檔引導優化,或者是否已通過分析工具(如*vsinstr.exe*或*vsperfmon.exe)* 進行檢測。

說明&mdash;如果組件已完成另一個程式碼剖析工具的檢測或最佳化，程式碼涵蓋範圍分析會略過該組件。 無法在此類組件上執行程式碼涵蓋範圍分析。

解決方式&mdash;關閉最佳化並使用新的組建。

### <a name="code-is-not-managed-net-or-native-c-code"></a>程式碼不是 Managed (.NET) 或機器碼 (C++)

分析&mdash;確認您在執行受控碼或 C++ 程式碼的某些測試。

說明&mdash;在 Visual Studio 中的程式碼涵蓋範圍分析只適用於受控碼和機器碼 (C++)。 如果您使用協力廠商工具，部分或所有程式碼可能會在不同平台上執行。

解決方式&mdash;無法使用。

### <a name="assembly-has-been-installed-by-ngen"></a>NGen 已安裝組件

分析&mdash;確認該組件不是從原生映像快取載入的。

說明&mdash;基於效能考量，不會分析原生映像組件。 如需詳細資訊，請參閱 [Ngen.exe (原生映像產生器)](/dotnet/framework/tools/ngen-exe-native-image-generator)。

解決方式&mdash;使用組件的 MSIL 版本。 請不要用 NGen 處理。

### <a name="custom-runsettings-file-with-bad-syntax"></a>語法不正確的自訂 .runsettings 檔案

分析&mdash;如果您使用的是自訂 *.runsettings* 檔案，其中可能包含語法錯誤。 程式碼涵蓋範圍未執行，且程式碼涵蓋範圍視窗在測試回合結束時未開啟，或是顯示舊的結果。

說明&mdash;您可以使用自訂 *.run 設定*檔運行單元測試以配置代碼覆蓋率選項。 這些選項可讓您包含或排除檔案。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

解決方式&mdash;可能發生兩種類型的錯誤：

- **XML 錯誤**

     在可視化工作室 XML 編輯器中打開 *.run 設定*檔。 尋找錯誤。

- **規則運算式錯誤**

  檔案中的每個字串都是規則運算式。 檢閱每一個錯誤，特別要尋找：

  - 不對稱的括號 (...) 或未逸出的括號 \\(...\\)。 如果要比對搜尋字串中的括號，必須逸出該括號。 例如，比對函式的用法： `.*MyFunction\(double\)`

  - 運算式開頭的星號或加號。 若要比對任何字元字串，請在星號後面加上點：`.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>自訂 .runsettings 檔包含不正確的排除項

分析&mdash;如果您使用自訂 *.runsettings* 檔，請確定該檔案包含您的組件。

說明&mdash;您可以使用自訂 *.run 設定*檔運行單元測試以配置代碼覆蓋率選項。 這些選項可讓您包含或排除檔案。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

解析&mdash;度`Include`從 *.run 設定*檔中刪除所有`Exclude`節點,然後刪除所有節點。 如果這樣可以解決問題，請將它們放回階段。

確定 DataCollectors 節點有指定 [程式碼涵蓋範圍]。 請將它和[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)中的範例比較。

## <a name="some-code-is-always-shown-as-not-covered"></a>某些程式碼一定會顯示為不涵蓋

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>原生 DLL 中的初始化程式碼會在檢測之前執行

分析&mdash;在靜態連結機器碼中，即使程式碼已執行，有時仍會將部分的初始化函式 **DllMain** 及它所呼叫的程式碼顯示為未涵蓋。

說明&mdash;程式碼涵蓋範圍工具的運作方式是，在應用程式開始執行之前將測試設備插入組件中。 在這之前載入的任何組件中，**DllMain** 中的初始化程式碼會於組件載入，以及應用程式執行之前時執行。 該程式碼會顯示為未涵蓋，這通常適用於靜態載入的組件。

解決方式&mdash;無。

## <a name="see-also"></a>另請參閱

- [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
