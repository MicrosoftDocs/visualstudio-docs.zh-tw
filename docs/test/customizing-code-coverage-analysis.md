---
title: 在 Visual Studio 中自訂程式碼涵蓋範圍分析
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52e2465a1e0a25e852073dc39a8aee18a6b47d7e
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295343"
---
# <a name="customize-code-coverage-analysis"></a>自訂程式碼涵蓋範圍分析

根據預設，程式碼涵蓋範圍會分析在單元測試期間載入的所有方案組件。 建議您使用此預設行為，因為大部分時間都可以運作良好。 如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

若要從程式碼涵蓋範圍結果中排除測試程式碼，並且只包括應用程式程式碼，請將 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 屬性新增至測試類別。

若要包括不屬於您方案的組件，請取得這些組件的 .pdb 檔案，並將這些檔案複製到組件 .dll 檔案的相同資料夾。

## <a name="run-settings-file"></a>回合設定檔

[回合設定檔](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)是單元測試工具所使用的組態檔。 *.runsettings* 檔案中會指定進階的程式碼涵蓋範圍設定。

若要自訂程式碼涵蓋範圍，請遵循下列步驟：

1. 將回合設定檔新增至方案。 在 [方案總管] 中，於方案的捷徑功能表上，選擇 [新增] > [新增項目]，然後選取 [XML 檔案]。 儲存檔案，其名稱的格式必須是 CodeCoverage.runsettings。

1. 新增本文結尾處範例檔中的內容，然後遵循下列各節中的描述並根據您自己的需求進行自訂。

1. 若要選取回合設定檔，請在 [測試] 功能表上，選擇 [測試設定] > [選取測試設定檔]。 若要指定從命令列或組建工作流程中執行測試的回合設定檔，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file)。

   當您選取 [分析程式碼涵蓋範圍] 時，從回合設定檔讀取組態資訊。

   > [!TIP]
   > 當您執行測試或更新程式碼時，並不會自動隱藏之前的程式碼涵蓋範圍結果及程式碼著色。

若要開啟和關閉自訂設定，請在 [測試] > [測試設定] 功能表中取消選取或選取檔案。

![具有自訂設定檔的測試設定功能表](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>指定符號搜尋路徑

程式碼涵蓋範圍需要組件的符號檔 (.pdb 檔案)。 在您的方案所建置的組件中，符號檔通常會和二進位檔一起出現，而且程式碼涵蓋範圍會自動運作。 但是在某些情況下，您可以在程式碼涵蓋範圍分析中加入參考的組件。 在此類情況下，.pdb 檔案不可以和二進位檔同時出現，不過您可以在 .runsettings 檔案中指定符號搜尋路徑。

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> 符號解析可能需要一些時間，特別是在使用具有許多組件的遠端檔案位置時。 因此，請考慮將 .pdb 檔案複製到二進位 (.dll 和 .exe) 檔案在本機中的位置。

### <a name="exclude-and-include"></a>排除和包含

您可以在程式碼涵蓋範圍分析中排除指定的組件。 例如: 

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

或者，您可以指定應包含的組件。 這種方法的缺點是，當您將其他組件加入至方案時，必須記得將它們加入至清單：

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

如果 **Include** 是空的，則程式碼涵蓋範圍處理會包括所有已載入以及可以找到其 .pdb 檔案的組件。 程式碼涵蓋範圍不包含與 **Exclude** 清單中子句相符的項目。

**Include** 是在 **Exclude** 之前處理。

### <a name="regular-expressions"></a>規則運算式

包含和排除節點使用規則運算式。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。 規則運算式與萬用字元不同。 特別之處在於：

- **.\\*** 會比對任何字元的字串

- **\\.** 會比對點 "."

- **\\(\\)** 會比對括弧 "(  )"

- **\\\\** 會比對檔案路徑分隔符號 "\\"

- **^** 會比對字串的開頭

- **$** 會比對字串的結尾

所有相符項目皆不區分大小寫。

例如: 

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

> [!WARNING]
> 如果規則運算式出現錯誤 (例如未逸出或不成對的括弧)，則不會執行程式碼涵蓋範圍分析。

### <a name="other-ways-to-include-or-exclude-elements"></a>包含或排除項目的其他方法

- **ModulePath** - 比對組件檔案路徑所指定的組件。

- **CompanyName** - 會依 **Company** 屬性比對組件。

- **PublicKeyToken** - 會依公開金鑰權杖比對已簽署的組件。

- **Source** - 依原始檔案路徑名稱的定義方式比對項目。

- **Attribute** - 比對附加特定屬性的項目。 指定屬性的完整名稱，並在名稱結尾包括 "Attribute"。

- **Function** - 依完整名稱比對程序、函式或方法。 若要比對函式名稱，規則運算式必須符合函式的完整名稱，包括命名空間、類別名稱、方法名稱和參數清單。 例如: 

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

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
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
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
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
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
- [對程式碼進行單元測試](../test/unit-test-your-code.md)