---
title: 針對 Visual Studio 中的程式碼涵蓋範圍進行疑難排解
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6224e03e4aafe152107a8fa7da56dc6bd8def1e3
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380547"
---
# <a name="troubleshoot-code-coverage"></a>對程式碼涵蓋範圍進行疑難排解

Visual Studio 中的程式碼涵蓋範圍分析工具會收集原生組件和 Managed 組件 (*.dll* 或 *.exe* 檔) 的資料。 不過，在某些情況下，[程式碼涵蓋範圍結果] 視窗會顯示類似「產生空白的結果:...」的錯誤。有幾種原因可能會導致您取得空的結果。 本文可協助您解決這些問題。

## <a name="what-you-should-see"></a>您應該會看見

如果您選擇 [測試] 功能表上的 [分析程式碼涵蓋範圍] 命令，而且組建和測試皆順利執行，則您應該會在 [程式碼涵蓋範圍] 視窗中看見結果清單。 您可能必須展開項目才能查看詳細資料。

![顯示著色內容的程式碼涵蓋範圍結果](../test/media/codecoverage1.png)

如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>看不見任何結果或看見舊結果的可能原因

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>您的 Visual Studio 版本是否正確?
 您需具備 Visual Studio 企業版。

### <a name="no-tests-were-executed"></a>沒有執行過任何測試

分析&mdash;請查看輸出視窗。 在 [顯示輸出來源] 下拉式清單中選擇 [測試]。 檢查是否有記錄任何警告或錯誤。

說明&mdash;程式碼涵蓋範圍分析會在執行測試時進行。 這項分析只包括在執行測試時載入記憶體的組件。 如果沒有執行任何測試，程式碼涵蓋範圍就不會產生任何報告。

解決方式&mdash;在 [測試總管] 中，選擇 [全部執行]，確認所執行的測試是否成功。 在使用 [分析程式碼涵蓋範圍] 之前修正所有錯誤。

### <a name="youre-looking-at-a-previous-result"></a>您看到的是之前的結果

當您修改並重新執行測試時，可能仍會顯示先前的程式碼涵蓋範圍結果，包括在先前執行時著色的程式碼。

1.  執行 [分析程式碼涵蓋範圍]。

2.  請務必在 [程式碼涵蓋範圍結果] 視窗中選取最新的一組結果。

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (符號) 檔案無法使用

分析&mdash;開啟編譯目標資料夾 (通常是 *bin\debug*)，然後針對每個組件確認 *.dll* 或 *.exe* 檔案所在的目錄中有 *.pdb* 檔案。

說明&mdash;程式碼涵蓋範圍引擎會要求每個組件在測試回合期間都能夠存取其相關聯的 *.pdb* 檔案。 如果特定組件沒有 *.pdb* 檔，就不會分析該組件。

產生 *.pdb* 檔的組建必須是產生 *.dll* 或 *.exe* 檔案的組建。

解決方式&mdash;請確定您的組建設定會產生 *.pdb* 檔。 如果建置專案時沒有更新 *.pdb* 檔案，請開啟專案屬性，選取 [組建] 頁面，選擇 [進階]，然後檢查 [偵錯資訊]。

如果 *.pdb* 和 *.dll* 或 *.exe* 檔案在不同的位置，請將 *.pdb* 檔複製到同一個目錄中。 將程式碼涵蓋範圍引擎設定成搜尋另一個位置的 *.pdb* 檔也是可行的。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

### <a name="use-an-instrumented-or-optimized-binary"></a>使用已檢測或最佳化的二進位檔

分析&mdash;判斷該二進位檔是否已完成「特性指引最佳化」等任何形式的進階最佳化，或者是否已完成 *vsinstr.exe* 或 *vsperfmon.exe* 等分析工具的檢測。

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

說明&mdash;您可以使用自訂 *.runsettings* 檔案執行單元測試．以設定程式碼涵蓋範圍選項。 這些選項可讓您包含或排除檔案。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

解決方式&mdash;可能發生兩種類型的錯誤：

-   **XML 錯誤**

     在 Visual Studio XML 編輯器中開啟 *.runsettings* 檔案。 尋找錯誤。

-   **規則運算式錯誤**

     檔案中的每個字串都是規則運算式。 檢閱每一個錯誤，特別要尋找：

    -   不對稱的括號 (...) 或未逸出的括號 \\(...\\)。 如果要比對搜尋字串中的括號，必須逸出該括號。 例如，比對函式的用法： `.*MyFunction\(double\)`

    -   運算式開頭的星號或加號。 若要比對任何字元字串，請在星號後面加上點：`.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>自訂 .runsettings 檔包含不正確的排除項

分析&mdash;如果您使用自訂 *.runsettings* 檔，請確定該檔案包含您的組件。

說明&mdash;您可以使用自訂 *.runsettings* 檔案執行單元測試．以設定程式碼涵蓋範圍選項。 這些選項可讓您包含或排除檔案。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

解決方式&mdash;移除 *.runsettings* 檔中的所有 `Include` 節點，然後移除所有 `Exclude` 節點。 如果這樣可以解決問題，請將它們放回階段。

確定 DataCollectors 節點有指定 [程式碼涵蓋範圍]。 請將它和[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)中的範例比較。

## <a name="some-code-is-always-shown-as-not-covered"></a>某些程式碼一定會顯示為不涵蓋

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>原生 DLL 中的初始化程式碼會在檢測之前執行

分析&mdash;在靜態連結機器碼中，即使程式碼已執行，有時仍會將部分的初始化函式 **DllMain** 及它所呼叫的程式碼顯示為未涵蓋。

說明&mdash;程式碼涵蓋範圍工具的運作方式是，在應用程式開始執行之前將測試設備插入組件中。 在這之前載入的任何組件中，**DllMain** 中的初始化程式碼會於組件載入，以及應用程式執行之前時執行。 該程式碼會顯示為未涵蓋，這通常適用於靜態載入的組件。

解決方式&mdash;無。

## <a name="see-also"></a>另請參閱

- [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)