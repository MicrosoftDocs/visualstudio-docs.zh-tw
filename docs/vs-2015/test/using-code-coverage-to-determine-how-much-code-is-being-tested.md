---
title: 使用程式碼涵蓋範圍來決定所測試的程式碼數量 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
ms.assetid: 800fc739-acd2-4242-84cb-1d83b4d82cf9
caps.latest.revision: 38
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 737311167fc1f444d5c0f8a5d2c27e2fe321da75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851243"
---
# <a name="using-code-coverage-to-determine-how-much-code-is-being-tested"></a>使用程式碼涵蓋範圍來決定所測試的程式碼數量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要判斷單元測試等自動程式碼測試實際測試的專案程式碼比例，您可以使用 Visual Studio 程式碼涵蓋範圍功能。 為有效防範 Bug，您的測試應該要使用或「覆蓋」大部分的程式碼。

 程式碼涵蓋範圍分析適用於 Managed 程式碼 (CLI) 和 Unmanaged (機器碼)。

 當您使用 [測試總管] 執行測試方法程式時，可以選擇程式碼涵蓋範圍。 結果表會顯示程式碼在每個組件、類別和方法中執行的百分比。 此外，原始檔編輯器會顯示已測試的程式碼。

 ![顯示著色內容的程式碼涵蓋範圍結果](../test/media/codecoverage1.png "CodeCoverage1")

 **需求**

- Visual Studio Enterprise

### <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>在 [測試總管] 中分析單元測試的程式碼涵蓋範圍

1. 在 [測試]**** 功能表中選擇 [分析程式碼涵蓋範圍]****。

2. 若要查看已執行的行，請選擇 [ ![顯示程式碼涵蓋範圍著色] 圖示](../test/media/codecoverage-showcoloringicon.png "CodeCoverage-ShowColoringIcon")**顯示程式碼涵蓋範圍著色**。

     若要修改色彩或使用粗體格式，請選擇 [工具]****、[選項]****、[環境]****、[字型和色彩]****、[顯示設定: 文字編輯器]****。 在 [顯示項目]**** 下，調整 [涵蓋範圍] 項目。

3. 如果結果顯示涵蓋範圍較小，請檢查不會執行的部分程式碼，並撰寫更多測試來涵蓋這些項目。 開發小組通常以 80% 的程式碼涵蓋範圍為目標。 某些情況可以接受較小的涵蓋範圍。 例如，從標準範本產生之程式碼涵蓋範圍較小是可接受的。

> [!TIP]
> 若要取得準確的結果：
>
> - 請務必關閉編譯器最佳化。
>
>   如果使用 Unmanaged 程式碼 (機器碼)，請使用偵錯組建。
>   - 請務必為每個組件產生 .pdb (符號) 檔。
>
>   如果您沒有收到預期的結果，請參閱 [疑難排解程式碼涵蓋範圍](../test/troubleshooting-code-coverage.md)。 . 更新程式碼後不要忘記再次執行程式碼涵蓋範圍。 修改程式碼後或執行測試時，並不會自動更新涵蓋範圍結果和程式碼著色。

## <a name="reporting-in-blocks-or-lines"></a>區塊或行報告
 程式碼涵蓋範圍以「區塊」**(Block) 計算。 一個區塊是只有一個進入點及一個結束點的程式碼片段。  如果程式的控制流程在測試回合期間通過區塊，該區塊即屬於覆蓋的區塊。 區塊使用次數不會影響結果。

 您也可以選擇表格標題中的 [新增/移除資料行]****，以行為單位顯示結果。 如果測試回合執行任一程式碼行中的所有程式碼區塊，會以一行計算。 同時包含執行及未執行之程式碼區塊的行屬於部分行。

 某些使用者習慣以行計算，因為百分比較符合您在原始程式碼中看見的片段大小。 長區塊的計算也視同單一區塊，即便長區塊佔用許多行。

## <a name="managing-code-coverage-results"></a>管理程式碼涵蓋範圍結果
 [程式碼涵蓋範圍結果] 視窗通常會顯示最近執行的結果。 如果您變更測試資料，或者每次只執行部分測試，結果就會有所不同。

 [程式碼涵蓋範圍] 視窗也可用來檢視之前的結果，或是在其他電腦上得到的結果。

 您可以合併數個回合的結果，例如合併使用不同測試資料的回合。

- **若要檢視先前的結果集**，請從下拉式功能表中選取它。 當您開啟新的方案時，功能表會顯示暫存清單。

- **若要檢視上一個工作階段的結果**，請選擇 [匯入程式碼涵蓋範圍結果]****，瀏覽至方案中的 [TestResults] 資料夾，然後匯入 .coverage 檔案。

     如果在產生 .coverage 檔案之後變更過原始程式碼，涵蓋範圍著色可能會不正確。

- **若要以文字顯示結果**，請選擇 [匯出程式碼涵蓋範圍結果]****。 這樣會產生一個易讀的 .coveragexml 檔案，您可以使用其他工具處理這個檔案，也可以透過郵件傳送該檔案。

- **若要將結果傳送給他人**，請傳送 .coverage 檔案或匯出的 .coveragexml 檔案。 然後，他們就可以匯入您所傳送的檔案。 如果他們有相同版本的原始程式碼，就可以看見涵蓋範圍著色。

## <a name="merging-results-from-different-runs"></a>合併不同回合的結果
 在某些情況下，會根據測試資料使用程式碼中的不同區塊。 因此，建議您合併不同測試回合的結果。

 例如，假設您在執行輸入 "2" 的測試時發現特定函式的涵蓋範圍是 50%。 當您第二次輸入 "-2" 執行測試時，您會在涵蓋範圍著色檢視中看見涵蓋範圍多了另外的 50%。 現在您合併了兩個測試回合的結果，而報告和涵蓋範圍檢視也顯示涵蓋範圍是該函式的 100%。

 ![在程式碼涵蓋範圍視窗合併程式](../test/media/codecoverage-mergeicon.png "CodeCoverage-MergeIcon")**代碼涵蓋範圍結果**中使用 [合併] 按鈕的圖示。 您可以選擇最近的回合或匯入之結果的任何組合。 如果您要合併匯出的結果，必須先匯入結果。

 使用 [匯出程式碼涵蓋範圍結果]****，儲存合併作業的結果。

### <a name="limitations-in-merging"></a>合併的限制

- 如果您從不同版本的程式碼合併涵蓋範圍資料，結果會個別顯示而不會合併。 若要取得完整的合併結果，請使用相同組建的程式碼，只變更測試資料。

- 如果合併先匯出再匯入的結果，您只能依行而不是依區塊檢視結果。 使用 [新增/移除資料行]**** 命令顯示行資料。

- 如果您合併 ASP.NET 專案測試的結果，會顯示個別測試的結果而非合併的結果。 這只適用於 ASP.NET 成品本身：會合併其他任何組件的結果。

## <a name="excluding-elements-from-the-code-coverage-results"></a>在程式碼涵蓋範圍結果中排除項目
 如果程式碼是從文字範本產生的，您可能會想要將程式碼中的特定項目從排除涵蓋範圍分數中排除。 將 `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` 屬性加入至下列任一程式碼項目：類別、結構、方法、屬性、屬性 setter 或 getter、事件。 請注意，排除類別並不會排除其衍生類別。

 例如：

```csharp

using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }

```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class

```

```cpp#
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }

}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }

```

### <a name="excluding-elements-in-native-c-code"></a>排除原生 C++ 程式碼中的項目
 排除 C++ 程式碼中的 Umanaged (原生) 項目：

```cpp

#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)

```

 使用下列巨集：

 `ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

 `ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* 是任何唯一名稱。

- *FunctionName* 是完整函式名稱。 可以包含萬用字元。 例如，若要排除某個類別的所有函式，可以寫成 `MyNamespace::MyClass::*`

- *SourceFilePath* 是 .cpp 檔案的本機或 UNC 路徑。 可以包含萬用字元。 下列範例會排除特定目錄中的所有檔案： `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- 請呼叫全域命名空間中的排除巨集，而不要呼叫任何命名空間或類別中的排除巨集。

- 您可以在單元測試程式碼檔案或應用程式程式碼檔案中排除。

- 您必須設定編譯器選項或使用 `#pragma managed(off)` 將排除編譯為 Unmanaged (機器碼)。

> [!NOTE]
> 若要排除 C++/CLI 程式碼中的函式，請將 `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` 屬性套用至該函式。 這和 C# 的做法相同。

### <a name="including-or-excluding-additional-elements"></a>包含或排除其他項目
 程式碼涵蓋範圍分析只能對載入的組件或與 .dll 或 .exe 檔案位於同一個目錄中的 .pdb 檔案執行。 因此，在某些情況下，您可以藉由取得包含適當 .pdb 檔案的複本來擴充所包含的組件集。

 您可以撰寫 .runsettings 檔案進一步控制執行程式碼範圍分析時選取的組件和項目。 例如，您可以排除特定種類的組件，而不需要在其類別中加入屬性。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

## <a name="analyzing-code-coverage-in-the-build-service"></a>在組建服務中分析程式碼涵蓋範圍
 當您檢查程式碼時，您的測試會在組建伺服器上與其他小組成員的所有其他測試一起執行。  (如果您尚未設定此功能，請參閱 [在組建程式中執行測試](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)。 ) 在組建服務上分析程式碼涵蓋範圍是很有用的，因為這可提供整個專案中涵蓋範圍的最新完整資訊。 這項分析也包含自動化系統測試，和通常不會在開發電腦上執行的其他自動程式碼測試。

1. 在 Team Explorer 中開啟 [組建]****，然後新增或編輯組建定義。

2. 在 [流程]**** 頁面上，展開 [自動化測試]****、[測試來源]****、[回合設定]****。 將 [回合設定檔的類型]**** 設為 [已啟用程式碼涵蓋範圍]****。

    如果您有一個以上的測試來源定義，請針對每一個定義重複以上步驟。

   - <em>但是沒有名為 [回合*配置檔案類型] 的</em>欄位*。 *

      在 [自動化測試]**** 下，選取 [測試組件]****，然後選擇行末的省略符號按鈕 [...]****。 在 [加入/編輯測試回合]**** 對話方塊中，選擇 [測試執行器]**** 之下的 [Visual Studio 測試執行器]****。

   ![設定程式碼涵蓋範圍的組建定義](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")

   組建執行後會將程式碼涵蓋範圍結果附加至測試回合，而且結果會出現在組建摘要。

## <a name="analyzing-code-coverage-in-a-command-line"></a>在命令列中分析程式碼涵蓋範圍
 若要從命令列執行測試，請使用 vstest.console.exe。 程式碼涵蓋範圍是此公用程式的選項。 如需詳細資訊，請參閱 [VSTest.Console.exe 命令列選項](https://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11)。

1. 啟動 Visual Studio Developer 命令提示字元：

     在 Windows 的 [開始]**** 功能表上，依序選擇 [所有程式]****、[Microsoft Visual Studio]****、[Visual Studio Tools]****、[開發人員命令提示字元]****。

2. 執行：

     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshooting"></a>疑難排解
 如果您沒有看見程式碼涵蓋範圍結果，請參閱[針對程式碼涵蓋範圍進行疑難排解](../test/troubleshooting-code-coverage.md)。

## <a name="external-resources"></a>外部資源

### <a name="guidance"></a>指引
 [使用 Visual Studio 2012 測試持續傳遞 – 第 2 章：單元測試：測試內部](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>另請參閱
 [自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)[疑難排解程式碼涵蓋範圍](../test/troubleshooting-code-coverage.md)[單元測試您的程式碼](../test/unit-test-your-code.md)
