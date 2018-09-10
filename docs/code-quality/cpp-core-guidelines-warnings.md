---
title: C + + Core Guidelines 的警告
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- cplusplus
ms.openlocfilehash: 035f1fe305576eb7f5bf05fb6cc5f6343e256dca
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279746"
---
# <a name="using-the-c-core-guidelines-checkers"></a>使用 c + + Core Guidelines 檢查工具
C + + Core Guidelines 是可攜性的集合的指導方針、 規則和關於 c + + 專家和設計工具所建立的 c + + 中撰寫程式碼的最佳作法。 Visual Studio 目前支援 c + + 做為其程式碼分析工具的一部分，這些規則的子集。 在 Visual Studio 2017 中，預設會安裝核心指南檢查工具，並會[以 Visual Studio 2015 的 NuGet 套件形式提供](#vs2015_corecheck)。

## <a name="the-c-core-guidelines-project"></a>C + + Core Guidelines 的專案
 C + + Core Guidelines Bjarne Stroustrup 和其他人所建立，是安全且有效地使用新式 c + + 的指南。 指導方針強調靜態型別安全和資源的安全。 它們會找出方法來消除或是減少最容易出錯的組件的語言，並建議如何簡化您的程式碼，以及更好的效能，可靠的方式。 這些指導方針是由標準 c + + Foundation 維護。 若要進一步了解，請參閱文件中， [c + + Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)，並存取 c + + Core Guidelines 的文件的專案檔上[GitHub](https://github.com/isocpp/CppCoreGuidelines)。

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>啟用程式碼分析的 c + + Core Check 指導方針
 您也可以選取您的專案上啟用程式碼分析**建置時啟用程式碼分析**核取方塊**程式碼分析**一節**屬性頁**對話方塊您的專案。

 ![程式碼分析的一般設定 屬性頁](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 C + + Core Check 規則是預設的規則集執行時啟用程式碼分析延伸模組。 由於 c + + Core Check 規則在開發期間，某些規則堅實的建立，而某些可能不是可供使用的所有程式碼，但可能仍有幫助。 規則分為兩個群組： 發行和實驗性。 您可以選擇是否要為您的專案屬性中執行的已釋出或實驗性的規則。

 ![程式碼分析延伸模組設定的屬性頁](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 若要啟用或停用 c + + Core Check 規則集，請開啟**屬性頁**為您的專案 對話方塊。 底下**組態屬性**，展開**程式碼分析**，**延伸**。 下拉式清單中控制項旁**啟用 c + + Core Check （發行）** 或**啟用 c + + Core Check （實驗性）**，選擇**是**或是**否**。 選擇 **[確定]** 或是**套用**以儲存變更。

## <a name="examples"></a>範例
 以下是一些的 c + + Core Check 規則可以找到問題的範例：

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

 此範例會示範幾個可以找到的 c + + Core Check 規則的警告：

-   C26494 是規則 Type.5： 一律初始化物件。

-   C26485 是規則 Bounds.3： 沒有陣列到指標 」 衰減。

-   C26481 是規則 Bounds.1： 不使用指標算術。 請改用 `span`。

 如果安裝和啟用，當您編譯此程式碼時前, 兩個警告皆為輸出，但會隱藏第三個 c + + Core Check 的程式碼分析規則集。 以下是範例程式碼的組建輸出：

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C + + Core Guidelines 是為了幫助您撰寫更好且更安全的程式碼。 不過，如果您有一個規則或設定檔不應該套用的位置執行個體，很容易就能直接在程式碼中隱藏它。 您可以使用`gsl::suppress`讓 c + + Core Check 偵測和報告任何違反規則，以下列程式碼區塊中的屬性。 您可以將標記個別的陳述式，以隱藏特定的規則。 您甚至可以隱藏整個 「 範圍 」 設定檔，藉由撰寫`[[gsl::suppress(bounds)]]`且不包含特定的規則數目。

## <a name="supported-rule-sets"></a>支援的規則集
當新規則加入至 c + + 核心指南檢查工具時，可能會增加預先存在的程式碼所產生的警告數目。 若要篩選哪些類型的規則，來啟用，您可以使用預先定義的規則集。 截至 Visual Studio 2017 15.3 版，是支援的規則集：
  - **擁有者指標規則**強制[擁有者相關的資源管理檢查<T>c + + Core guidelines 的](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **常數規則**強制[c + + Core guidelines 的常數相關檢查](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)。

  - **原始指標規則**強制[資源管理檢查 c + + Core guidelines 的相關原始指標](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **唯一指標規則**強制[資源管理檢查與 c + + Core guidelines 的類型具有唯一指標語意](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **界限規則**強制[界限的 c + + Core Guidelines 的設定檔](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

  - **輸入規則**強制[輸入設定檔的 c + + Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)。


 您可以選擇限制只有一個或幾個群組的警告。 **原生最小**並**原生建議**規則集包括 c + + Core Check 規則，除了其他 PREfast 的檢查。 若要查看可用規則集，請開啟 [專案屬性] 對話方塊中，選取**程式碼 Analysis\General**，開啟下拉式清單中的**規則集**下拉式方塊中，並挑選**選擇多個規則集**. 如需使用 Visual Studio 中的規則集的詳細資訊，請參閱[使用規則集分組程式碼分析規則](using-rule-sets-to-group-code-analysis-rules.md)。

## <a name="macros"></a>巨集
 C + + 核心指南檢查工具隨附的標頭檔會定義巨集可讓您更輕鬆地隱藏整個類別的程式碼中的警告：

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

這些巨集對應至規則集，然後展開為以空格分隔的清單的警告編號。 您可以使用適當的 pragma 建構來設定有效的規則集也就是有趣的專案或程式碼區段。 在下列範例中，程式碼分析將只會警告有關遺漏常數的修飾詞：

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>屬性
 Microsoft Visual c + + 編譯器會有有限的支援 GSL 隱藏屬性。
它可用來隱藏在運算式和函式內的區塊陳述式的警告。

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>使用命令列選項隱藏分析
 而不是 #pragmas，您可以使用命令列選項的檔案屬性頁中，隱藏警告的專案或單一檔案。 例如，若要停用警告 26400 檔案：

 1) 以滑鼠右鍵按一下 [檔案中的**方案總管]**

 2) 選擇**屬性 |C / C + + |命令列**

 3) 在 [**其他選項**] 視窗中，新增`/wd26400`。

 您可以使用命令列選項，暫時停用檔案的所有程式碼分析，藉由指定`/analyze-`。 這會產生警告*D9025 覆寫 '/analyze' 與 ' /analyze-'*，這會提醒您，稍後重新啟用程式碼分析。

 ## <a name="corecheck_per_file"></a> 啟用特定專案檔中，c + + Core 指導方針檢查工具
有時候可能蠻有用已取得焦點的執行程式碼分析，仍然繼續利用 Visual Studio IDE。 以下是範例案例可針對大型專案以儲存建置階段，並讓它更容易篩選結果。
1.  在命令殼層設定`esp.extension`和`esp.annotationbuildlevel`環境變數。
2.  啟動 Visual Studio，從命令殼層繼承這些變數。
3.  載入您的專案，並開啟其內容。
4.  啟用程式碼分析，挑選適當的規則集，但不是啟用程式碼分析延伸模組。
5.  請移至您想要分析使用 c + + 核心指南檢查工具並開啟其內容的檔案。
6.  選擇**C / C + + \Command 列選項**並新增 `/analyze:plugin EspXEngine.dll`
7.  停用的先行編譯標頭 (**C / C + + 標頭 \Precompiled**)。 這是必要的因為延伸模組引擎可能會嘗試從先行編譯標頭讀取其內部的資訊，而且後者以編譯專案的預設選項，如果它不會相容。
8.  重建專案。 常見的 PREFast 檢查應該執行的所有檔案。 因為預設不啟用 c + + 核心指南檢查工具，它應該只執行上已設定為使用它的檔案。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>如何使用 c + + 核心指南檢查功能，Visual Studio 外部
您可以使用 c + + Core Guidelines 檢查自動化組建中。

### <a name="msbuild"></a>MSBuild
 原生程式碼分析檢查程式 (PREfast) 已整合到 MSBuild 環境所自訂的目標檔案。 您可以使用專案屬性來啟用它，並新增 c + + 核心指南檢查工具 （此作業取決於 PREfast）：

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
請確定您新增這些屬性，才能匯入 Microsoft.Cpp.targets 檔案。 您可以挑選特定的規則集或建立自訂規則集，或使用預設規則集包含其他 PREfast 的檢查。

您也可以使用相同的方法為只在指定的檔案上執行 c + + Core Checker[稍早所述](#coreckeck_per_file)，但是使用 MSBuild 檔案。 可以透過設定環境變數`BuildMacro`項目：

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

如果您不想修改專案檔，您可以在命令列上傳遞內容：

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>非 MSBuild 專案
如果您使用不依賴 MSBuild 的建置系統仍然可以執行 「 檢查 」，但您必須熟悉程式碼分析引擎設定 （這不保證在未來支援） 的某些內部項目。

您必須設定一些環境變數，並使用適當的命令列選項，編譯器。 最好是能夠 「 Native Tools 命令提示字元 」 環境下，讓您不需要搜尋特定編譯器的路徑，包括目錄等等。

1.  **環境變數**
  - `set esp.extensions=cppcorecheck.dll` 這會告訴引擎載入的 c + + Core Guidelines 的模組。
  - `set esp.annotationbuildlevel=ignore` 這會停用邏輯會處理 SAL 註釋。 註解不會影響程式碼分析，在 c + + 核心指南檢查工具，但其處理的時間 （有時很多時間）。 此設定是選擇性的但強烈建議。
  - `set caexcludepath=%include%` 我們強烈建議您停用在標準標頭會引發警告。 您可以新增更多的路徑，例如常見的標頭，在您的專案中的路徑。
2.  **命令列選項**
  - `/analyze`  啟用程式碼分析 (考慮也使用 / 分析： 只和 /analyze: quiet)。
  - `/analyze:plugin EspXEngine.dll` 此選項會將程式碼分析延伸模組引擎載入 PREfast。 接著，這個引擎會載入 c + + 核心指南檢查工具。



## <a name="use-the-guideline-support-library"></a>使用指導方針的支援程式庫
 指導方針的支援程式庫可協助您遵循核心指導方針。 GSL 包含可讓您以更安全的替代項目取代出錯建構的定義。 例如，您可以取代`T*, length`的參數組`span<T>`型別。 將會位於 GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl)。 程式庫是開放原始碼，因此您可以檢視的來源、 註解，或提供。 專案，請參閱[ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)。

 ## <a name="vs2015_corecheck"></a> 在 Visual Studio 2015 專案中使用的 c + + Core Check 指導方針
  如果您使用 Visual Studio 2015，預設不會安裝 c + + Core Check 的程式碼分析規則集。 您可以啟用 Visual Studio 2015 中的 c + + Core Check 程式碼分析工具之前，您必須執行一些額外的步驟。 Microsoft Visual Studio 2015 專案提供支援，藉由使用 Nuget 套件。 封裝名為 Microsoft.CppCoreCheck，且可在[ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck)。 此封裝需要有至少安裝 Visual Studio 2015 Update 1。

 封裝也會安裝為相依性，僅限標頭的指導方針的支援程式庫 (GSL) 另一個套件。 GSL 也是在 GitHub 上的可用[ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)。

 由於程式碼分析規則已載入的方式，您必須安裝到每個您想要檢查 Visual Studio 2015 中的 c + + 專案的 Microsoft.CppCoreCheck NuGet 套件。

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>若要將 Microsoft.CppCoreCheck 套件新增至您的專案在 Visual Studio 2015

1.  在 [**方案總管] 中**，以滑鼠右鍵按一下您想要將封裝加入方案中開啟您專案的內容功能表。 選擇**管理 NuGet 套件**來開啟**NuGet 套件管理員**。

2.  在  **NuGet 套件管理員**視窗中，搜尋 Microsoft.CppCoreCheck。

     ![Nuget 套件管理員 視窗會顯示 CppCoreCheck 封裝](../code-quality/media/cppcorecheck_nuget_window.png)

3.  選取 Microsoft.CppCoreCheck 封裝，然後選擇**安裝** 按鈕，將規則新增至您的專案。

 NuGet 套件會將您的專案上啟用程式碼分析時，會叫用您專案中的其他的 MSBuild.targets 檔案。 這個.targets 檔案會將 c + + Core Check 規則做為額外的延伸模組加入至 Visual Studio 程式碼分析工具。 安裝套件時，您可以使用 [屬性頁] 對話方塊，啟用或停用發行和實驗性的規則。

