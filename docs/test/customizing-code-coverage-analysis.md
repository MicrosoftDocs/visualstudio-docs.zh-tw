---
title: 自訂程式碼涵蓋範圍分析
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ce63e6ff368b090f096642c7f664c1adf45a0857
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880308"
---
# <a name="customize-code-coverage-analysis"></a>自訂程式碼涵蓋範圍分析

根據預設，程式碼涵蓋範圍會分析在單元測試期間載入的所有方案組件。 建議您使用此預設行為，因為大部分時間都可以運作良好。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

若要從程式碼涵蓋範圍結果中排除測試程式碼，並且只包括應用程式程式碼，請將 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 屬性新增至測試類別。

若要包括不屬於您方案的組件，請取得這些組件的 .pdb** 檔案，並將這些檔案複製到組件 .dll** 檔案的相同資料夾。

## <a name="run-settings-file"></a>回合設定檔

[運行設定檔](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)是單元測試工具使用的設定檔。 高級代碼覆蓋率設置在 *.run設置*檔中指定。

若要自訂程式碼涵蓋範圍，請遵循下列步驟：

1. 將回合設定檔新增至方案。 在**解決方案資源管理員**中,在解決方案的快捷選單上,選擇 **「新增新** > **項目**」,然後選擇**XML 檔**。 儲存檔案，其名稱的格式必須是 CodeCoverage.runsettings**。

2. 新增本文結尾處範例檔中的內容，然後遵循下列各節中的描述並根據您自己的需求進行自訂。

::: moniker range="vs-2017"

3. 若要選取回合設定檔，請在 [測試]**** 功能表上，選擇 [測試設定]**** > [選取測試設定檔]****。 若要指定從命令列執行測試的回合設定檔，請參閱[設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line)。

::: moniker-end

::: moniker range=">=vs-2019"

3. 要選擇執行設定檔,請在 **「測試」** 選單上選擇 **「選擇設定檔**」 。 若要指定從命令列執行測試的回合設定檔，請參閱[設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line)。

::: moniker-end

   當您選取 [分析程式碼涵蓋範圍]**** 時，從回合設定檔讀取組態資訊。

   > [!TIP]
   > 當您執行測試或更新程式碼時，並不會自動隱藏任何之前的程式碼涵蓋範圍結果及程式碼著色。

::: moniker range="vs-2017"

若要開啟和關閉自訂設定，請在 [測試]**[測試設定]** > **** 功能表中取消選取或選取檔案。

![Visual Studio 2017 中具有自訂設定檔的測試設定功能表](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

要關閉和打開自訂設定,請取消選擇或選擇 **「測試」** 選單上的檔案。

::: moniker-end

## <a name="symbol-search-paths"></a>符號搜尋路徑

程式碼涵蓋範圍需要組件的符號檔 (.pdb** 檔案)。 在您的方案所建置的組件中，符號檔案通常會和二進位檔一起出現，而且程式碼涵蓋範圍會自動運作。 在某些情況下，您可以在程式碼涵蓋範圍分析中加入參考的組件。 在這種情況下 *,.pdb*檔案可能不靠近二進位檔案,但您可以在 *.runsettings*檔中指定符號搜索路徑。

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> 符號解析可能需要一些時間，特別是在使用具有許多組件的遠端檔案位置時。 因此，請考慮將 .pdb** 檔案複製到二進位 (.dll** 和 .exe**) 檔案在本機中的位置。

## <a name="include-or-exclude-assemblies-and-members"></a>包括或排除程式集和成員

您可以在程式碼覆蓋率分析中包括或排除程式集或特定類型和成員。 如果 **「包括」** 部分為空或省略,則包括載入並具有關聯的 PDB 檔的所有程式集。 如果程式集或成員與 **「排除」** 部分中子句匹配,則從代碼覆蓋率中排除該子句。 **"排除**"部分優先於"**包括**"部分:如果程式集同時列在 **"包括"** 和"**排除"** 中,則該程式集將不包含在代碼覆蓋率中。

例如,以下 XML 透過指定單個程式集的名稱來排除其名稱:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

以下範例指定代碼覆蓋率中應只包含單個程式集:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

下表顯示了程式集和成員可以匹配以包含在代碼覆蓋率中或排除代碼覆蓋率的各種方式。

| XML 元素 | 符合的內容 |
| - | - |
| ModulePath | 符合程式集名稱或檔路徑指定的程式集。 |
| CompanyName | 按 **"公司"** 屬性匹配程式集。 |
| PublicKeyToken | 按公開金鑰的權集。 |
| 來源 | 依定義元素的源檔的路徑名稱匹配元素。 |
| 屬性 | 匹配具有指定屬性的元素。 指定屬性的完整名稱，例如 `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`。<br/><br/>如果您排除 <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> 屬性，則會從程式碼涵蓋範圍分析中排除使用語言功能 (例如 `async`、`await`、`yield return`) 和自動實作屬性的程式碼。 若要排除真正產生的程式碼，只要排除 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 屬性即可。 |
| 函式 | 按完全限定的名稱(包括參數清單)匹配過程、函數或方法。 您還可以使用[正規表示式](#regular-expressions)匹配名稱的一部分。<br/><br/>範例：<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)`(C++) |

### <a name="regular-expressions"></a>規則運算式

包含和排除節點使用與萬用字元不同的規則運算式。 所有相符項目皆不區分大小寫。 部份範例如下：

- **.\*** 符合任何字元的字串

- **\\.** 會比對點 "."

- ( ) 匹配括弧 "()" ** \\ \\ **

- **\\\\**符合檔案路徑分隔符"\\

- **^** 符合字串的開頭

- **$** 符合字串的末尾

以下 XML 簡用如何使用正規表示式包括與排除特定程式集:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

以下 XML 簡用如何使用正規表示式包括與排除特定函數:

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> 如果規則運算式出現錯誤 (例如未逸出或不成對的括弧)，則不會執行程式碼涵蓋範圍分析。

有關正規表示式的詳細資訊,請參閱在[Visual Studio 中使用正規表示式](../ide/using-regular-expressions-in-visual-studio.md)。

## <a name="sample-runsettings-file"></a>範例 .runsettings 檔案

複製此程式碼，並根據需求編輯。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>另請參閱

- [使用回合設定檔設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [單元測試代碼](../test/unit-test-your-code.md)
