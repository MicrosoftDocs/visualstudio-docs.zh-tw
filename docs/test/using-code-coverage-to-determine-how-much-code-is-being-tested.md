---
title: 程式碼涵蓋範圍測試
description: 瞭解如何使用 Visual Studio 的程式碼涵蓋範圍功能，判斷程式碼測試要測試的專案程式碼比例。
ms.custom: SEO-VS-2020
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c74a39c81de2612bca5c3fc39286a4432916eb11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850070"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>使用程式碼涵蓋範圍來決定所測試的程式碼數量

若要判斷單元測試等自動程式碼測試實際測試的專案程式碼比例，您可以使用 Visual Studio 程式碼涵蓋範圍功能。 為有效防範 Bug，您的測試應該要使用或「覆蓋」大部分的程式碼。

程式碼涵蓋範圍分析適用於 Managed 程式碼 (CLI) 和 Unmanaged (機器碼)。

當您使用 [測試總管] 執行測試方法程式時，可以選擇程式碼涵蓋範圍。 結果表會顯示程式碼在每個組件、類別和方法中執行的百分比。 此外，原始檔編輯器會顯示已測試的程式碼。

::: moniker range="vs-2017"

![顯示著色內容的程式碼涵蓋範圍結果](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>規格需求

程式碼涵蓋範圍功能僅適用於 Visual Studio Enterprise 版本。

## <a name="analyze-code-coverage"></a>分析程式碼涵蓋範圍

::: moniker range="vs-2017"

1. 在 [測試] 功能表中選擇 [分析程式碼涵蓋範圍]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [ **測試** ] 功能表上，選取 [ **分析所有測試的程式碼涵蓋範圍**]。

   ![在 VS 2019 中分析程式碼涵蓋範圍功能表](../test/media/vs-2019/analyze-code-coverage.png)

   您也可以從 Test Explorer 工具視窗執行程式碼涵蓋範圍。

::: moniker-end

2. 執行測試之後，若要查看已執行的行，請選擇 [顯示程式碼涵蓋 ![ 範圍著色] 圖示， ](../test/media/codecoverage-showcoloringicon.png) 在 [程式碼涵蓋範圍 **結果**] 視窗中 **顯示程式碼涵蓋範圍著色**。 依預設，測試所涵蓋的程式碼會以淺藍色反白顯示。

   > [!TIP]
   > 若要變更色彩或使用粗體臉部，請選擇 [**工具**  >  **選項**  >  **環境** 字型  >  **及色彩**  >  **顯示設定：文字編輯器**]。 在 [ **顯示專案**] 下，調整 [涵蓋範圍] 專案的設定，例如 [ **涵蓋範圍未觸及] 區域**。
   >
   > ![程式碼涵蓋範圍字型和色彩](media/vs-2019/coverage-fonts-and-colors.png)

3. 如果結果顯示涵蓋範圍較小，請檢查不會執行的部分程式碼，並撰寫更多測試來涵蓋這些項目。 開發小組通常以 80% 的程式碼涵蓋範圍為目標。 某些情況可以接受較小的涵蓋範圍。 例如，從標準範本產生之程式碼涵蓋範圍較小是可接受的。

> [!TIP]
> - 關閉編譯器優化
> - 如果您正在使用非受控 (原生) 程式碼，請使用 debug build
> - 為每個元件產生 .pdb (符號) 檔

如果沒有得到預期的結果，請參閱[針對程式碼涵蓋範圍進行疑難排解](../test/troubleshooting-code-coverage.md)。

更新程式碼後不要忘記再次執行程式碼涵蓋範圍。 修改程式碼後或執行測試時，並不會自動更新涵蓋範圍結果和程式碼著色。

## <a name="report-in-blocks-or-lines"></a>區塊或行報告

程式碼涵蓋範圍以「區塊」(Block) 計算。 一個區塊是只有一個進入點及一個結束點的程式碼片段。  如果程式的控制流程在測試回合期間通過區塊，該區塊即屬於覆蓋的區塊。 區塊使用次數不會影響結果。

您也可以選擇表格標題中的 [新增/移除資料行]，以行為單位顯示結果。 某些使用者習慣以行計算，因為百分比較符合您在原始程式碼中看見的片段大小。 長區塊的計算也視同單一區塊，即便長區塊佔用許多行。

> [!TIP]
> 程式碼行可以包含一個以上的程式碼區塊。 如果是這種情況，且測試回合執行程式碼行中的所有程式碼區塊，則會以一行計算。 如果執行了程式碼行中的部分 (而非全部) 程式碼區塊，則會計算為部分行。

## <a name="manage-code-coverage-results"></a>管理程式碼涵蓋範圍結果

[程式 **代碼涵蓋範圍結果** ] 視窗通常會顯示最近執行的結果。 如果您變更測試資料，或者每次只執行部分測試，結果就會有所不同。

[程式碼涵蓋範圍] 視窗也可用來檢視之前的結果，或是在其他電腦上得到的結果。

您可以合併數個回合的結果，例如合併使用不同測試資料的回合。

- **若要檢視先前的結果集**，請從下拉式功能表中選取它。 當您開啟新的方案時，功能表會顯示暫存清單。

- **若要查看上一個會話的結果**，請選擇 [匯 **入程式碼涵蓋範圍結果**]，流覽至方案中的 [ **TestResults** ] 資料夾，然後匯入 [ *涵蓋範圍* ] 檔案。

   如果原始程式碼自產生的 *涵蓋範圍* 以來已變更，涵蓋範圍著色可能會不正確。

- **若要以文字顯示結果**，請選擇 [匯出程式碼涵蓋範圍結果]。 這會產生一個可讀取的 *>.coveragexml* 檔案，您可以使用其他工具來處理這些檔案，或輕鬆地在 mail 中傳送。

- **若要將結果傳送給其他人**，請傳送 *.coverage* 檔案或匯出的 *>.coveragexml* 檔案。 然後，他們就可以匯入您所傳送的檔案。 如果他們有相同版本的原始程式碼，就可以看見涵蓋範圍著色。

## <a name="merge-results-from-different-runs"></a>合併不同回合的結果

在某些情況下，會根據測試資料使用程式碼中的不同區塊。 因此，建議您合併不同測試回合的結果。

例如，假設您在執行輸入 "2" 的測試時發現特定函式的涵蓋範圍是 50%。 當您第二次輸入 "-2" 執行測試時，您會在涵蓋範圍著色檢視中看見函式涵蓋範圍多了另外的 50%。 現在您合併了兩個測試回合的結果，而報告和涵蓋範圍檢視也顯示涵蓋範圍是該函式的 100%。

![在程式碼涵蓋範圍視窗 ](../test/media/codecoverage-mergeicon.png) **合併程式碼涵蓋範圍結果** 中使用 [合併] 按鈕的圖示。 您可以選擇最近的回合或匯入之結果的任何組合。 如果您要合併匯出的結果，必須先匯入結果。

使用 [匯出程式碼涵蓋範圍結果]，儲存合併作業的結果。

### <a name="limitations-in-merging"></a>合併的限制

- 如果您從不同版本的程式碼合併涵蓋範圍資料，結果會個別顯示而不會合併。 若要取得完整的合併結果，請使用相同組建的程式碼，只變更測試資料。

- 如果合併先匯出再匯入的結果，您只能依行而不是依區塊檢視結果。 使用 [新增/移除資料行] 命令顯示行資料。

- 如果您合併 ASP.NET 專案測試的結果，會顯示個別測試的結果而非合併的結果。 這只適用於 ASP.NET 成品本身：會合併其他任何組件的結果。

## <a name="exclude-elements-from-the-code-coverage-results"></a>在程式碼涵蓋範圍結果中排除項目

如果程式碼是從文字範本產生的，您可能會想要將程式碼中的特定項目從排除涵蓋範圍分數中排除。 將 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 屬性新增至下列任一程式碼項目：類別、結構、方法、屬性、屬性 setter 或 getter、事件。

> [!TIP]
> 排除類別並不會排除其衍生類別。

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

```cpp
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

### <a name="exclude-elements-in-native-c-code"></a>排除原生 C++ 程式碼中的項目

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

### <a name="include-or-exclude-additional-elements"></a>包含或排除其他項目

程式碼涵蓋範圍分析只會在已載入的元件上執行，而且可以在與 *.dll* 或 *.exe* 檔案相同的目錄中使用 *.pdb* 檔。 因此，在某些情況下，您可以藉由取得適當 *.pdb* 檔案的複本，來擴充所包含的元件集。

您可以藉由撰寫 *.runsettings* 檔案，更進一步掌控針對程式碼涵蓋範圍分析選取的元件和元素。 例如，您可以排除特定種類的組件，而不需要在其類別中加入屬性。 如需詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

## <a name="analyze-code-coverage-in-azure-pipelines"></a>在 Azure Pipelines 中分析程式碼涵蓋範圍

當您檢查程式碼時，您的測試會在組建伺服器上與其他小組成員的測試一起執行。 在 Azure Pipelines 中分析程式碼覆蓋範圍，可針對整個專案的覆蓋範圍取得最新、最完整的分析結果，因此它是非常有用的方法。 這項分析也包含自動化系統測試，和通常不會在開發電腦上執行的其他自動程式化測試。 如需詳細資訊，請參閱[使用您的組建執行單元測試](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)。

## <a name="analyze-code-coverage-from-the-command-line"></a>從命令列分析程式碼涵蓋範圍

若要從命令列執行測試，請使用 *vstest.console.exe*。 程式碼涵蓋範圍是 *vstest.console.exe* 公用程式的選項。

1. 啟動 Visual Studio 的開發人員命令提示字元：

   ::: moniker range="vs-2017"

   在 Windows 的 [開始] 功能表中，選擇 [Visual Studio 2017]**[VS 2017 開發人員命令提示字元]** > 。

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   在 Windows 的 [開始] 功能表中，選擇 [Visual Studio 2019]**[VS 2019 開發人員命令提示字元]** > 。

   ::: moniker-end

2. 在命令提示字元中執行以下命令：

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

如需詳細資訊，請參閱 [VSTest.Console.exe 命令列選項](vstest-console-options.md)。

## <a name="troubleshoot"></a>疑難排解

如果您看不到程式碼涵蓋範圍結果，[針對程式碼涵蓋範圍進行疑難排解](../test/troubleshooting-code-coverage.md)一文可能對您有所幫助。

## <a name="see-also"></a>另請參閱

- [自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)
- [對程式碼涵蓋範圍進行疑難排解](../test/troubleshooting-code-coverage.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)
