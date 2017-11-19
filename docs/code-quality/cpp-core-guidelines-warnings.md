---
title: "C + + 核心指導方針警告 |Microsoft 文件"
ms.custom: 
ms.date: 08/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 65f4e7ed865a3a620d58b45580914d6e0b589660
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="using-the-c-core-guidelines-checkers"></a>使用 c + + 核心指導方針 checker
C + + 核心指導方針是可攜式的一組成指導方針、 規則和關於 c + + 專家和設計工具所建立的 c + + 中撰寫程式碼的最佳作法。 Visual Studio 目前支援 c + + 做為其程式碼分析工具的一部分，這些規則的子集。 核心導線西洋棋安裝預設會在 Visual Studio 2017，而且[可做為 Visual Studio 2015 的 NuGet 套件](#vs2015_corecheck)。
  
## <a name="the-c-core-guidelines-project"></a>專案的 c + + 核心指導方針  
 Bjarne Stroustrup 和其他人所建立，c + + 核心指導方針是安全且有效地使用現代 c + + 的指引。 指導方針強調靜態型別安全和資源的安全。 這些識別的方式來消除或是減少最容易出錯的組件的語言，而且可靠的方式會建議如何簡化您的程式碼和更好的效能。 標準 c + + Foundation 會維護這些指導方針。 若要進一步了解，請參閱文件， [c + + 核心指導方針](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)，存取在 c + + 核心指導方針文件專案檔和[GitHub](https://github.com/isocpp/CppCoreGuidelines)。  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>啟用程式碼分析的 c + + 核心檢查指導方針  
 您也可以選取您的專案上啟用程式碼分析**建置時啟用程式碼分析**中的核取方塊**程式碼分析**區段**屬性頁**對話方塊您的專案。  
  
 ![程式碼分析的一般設定 屬性頁](../code-quality/media/cppcorecheck_codeanalysis_general.png "CPPCoreCheck_CodeAnalysis_General")  
  
 C + + 核心檢查 」 規則是預設的規則集時已啟用程式碼分析執行的擴充功能。 由於 c + + 核心檢查規則開發，全都堅實的某些規則和某些可能不是可供使用的所有程式碼，但仍有幫助。 規則分成兩個群組： 已釋放及實驗。 您可以選擇是否要為您的專案屬性中執行已釋出或實驗性規則。  
  
 ![程式碼分析延伸模組設定的屬性頁](../code-quality/media/cppcorecheck_codeanalysis_extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
 若要啟用或停用 c + + 核心檢查規則集，請開啟**屬性頁**為您的專案 對話方塊。 在下**組態屬性**，依序展開**程式碼分析**，**延伸**。 旁邊的下拉式清單中控制**檢查 （發行） 啟用 c + + 核心**或**檢查 （實驗） 啟用 c + + 核心**，選擇**是**或**否**。 選擇**確定**或**套用**以儲存變更。  
  
## <a name="examples"></a>範例  
 以下是範例的 c + + 核心檢查規則可以找到的問題：  
  
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
  
 這個範例會示範幾個可以找到的 c + + 核心檢查 」 規則的警告：  
  
-   C26494 是規則 Type.5： 一律初始化物件。  
  
-   C26485 是規則 Bounds.3： 沒有陣列至指標衰退。  
  
-   C26481 是規則 Bounds.1： 不要使用指標算術。 請改用 `span` 。  
  
 如果安裝和編譯此程式碼前, 兩個警告就是輸出，但是第三個隱藏時啟用 c + + 核心檢查程式碼分析規則集。 以下是範例程式碼的組建輸出：  
  
```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------  
1>  CoreCheckExample.cpp  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)  
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
```  
  
C + + 核心指導方針，會有幫助您撰寫更好且更安全的程式碼。 不過，如果您有位置不應該套用的規則或設定檔的執行個體時，很容易隱藏直接在程式碼中。 您可以使用`gsl::suppress`屬性，以避免 c + + 核心檢查偵測和報告的下列程式碼區塊中的規則的任何違規。 您可以將標記個別的陳述式，以隱藏特定規則。 您甚至可以隱藏整個 「 範圍 」 設定檔寫入`[[gsl::suppress(bounds)]]`不包括特定的規則數目。  

## <a name="supported-rule-sets"></a>支援的規則集
當新的規則加入至 c + + 核心指導方針檢查程式，可能會增加預先存在的程式碼會在產生的警告數目。 您可以使用預先定義的規則集來篩選要啟用的規則類型。 自 Visual Studio 2017 版本 15.3，支援的規則集是： 
  - **擁有者指標規則**強制[資源管理會檢查與擁有者相關<T>從 c + + 核心指引](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **Const 規則**強制[const 相關檢查從 c + + 核心指引](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)。

  - **原始指標規則**強制[資源管理會檢查從 c + + 核心指導方針的相關原始指標](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **唯一指標規則**強制[資源管理檢查 c + + 核心指導方針中相關類型的唯一指標語意](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)。

  - **範圍規則**強制[範圍的 c + + 核心指導方針的設定檔](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。

  - **輸入規則**強制[輸入設定檔的 c + + 核心指導方針](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)。


 您可以選擇限制的警告，只是一或數個群組。 **原生最小值**和**原生建議**規則集包含其他 PREfast 檢查除了 c + + 核心檢查的規則。 若要查看可用規則集，請開啟 [專案屬性] 對話方塊中，選取**程式碼 Analysis\General**，開啟下拉式清單中的**規則集**下拉式方塊中，並挑選**選擇多個規則集**. 如需有關使用 Visual Studio 中的規則集的詳細資訊，請參閱[使用規則集分組程式碼分析規則](using-rule-sets-to-group-code-analysis-rules.md)。

## <a name="macros"></a>巨集
 C + + 核心指導方針檢查隨附標頭檔會定義巨集可讓您更輕鬆地隱藏整個類別程式碼中的警告：

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

這些巨集對應到規則集，然後展開成的警告編號並以空格分隔清單。 您可以使用適當的 pragma 建構設定有效的規則集也就是有趣的專案或程式碼區段。 在下列範例中，程式碼分析會只警告遺漏常數的修飾詞：

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>屬性
 Microsoft Visual c + + 編譯器具有有限的支援 GSL 隱藏屬性。
它可以用來隱藏在運算式和函式內的區塊陳述式上的警告。

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

## <a name="suppressing-analysis-by-using-command-line-options"></a>使用命令列選項來隱藏分析
 而不是 #pragmas，您可以使用命令列選項的檔案屬性頁中，隱藏警告的專案或單一檔案。 例如，若要停用警告 26400 檔案：
 
 1) 中的檔案，以滑鼠右鍵按一下**方案總管**

 2) 選擇**屬性 |C / C + + |命令列**

 3) 在**其他選項**視窗中，加入`/wd26400`。

 您可以使用命令列選項，暫時停用所有的程式碼分析檔案，藉由指定`/analyze-`。 這會產生警告*D9025 覆寫 '/analyze' 與 ' /analyze-'*，這會提醒您，稍後重新啟用程式碼分析。

 ## <a name="corecheck_per_file"></a>啟用特定的專案檔案 c + + 核心指導方針檢查
有時可能會對已取得焦點的執行程式碼分析和仍然利用 Visual Studio IDE 很實用。 以下是範例案例可用於大型專案以儲存建置時間，並讓您更輕鬆地篩選結果。
1.  在命令殼層設定`esp.extension`和`esp.annotationbuildlevel`環境變數。
2.  啟動 Visual Studio，從命令殼層繼承這些變數。
3.  載入您的專案，並開啟其內容。
4.  啟用程式碼分析，挑選適當的規則集，但不是啟用程式碼分析擴充功能。
5.  移至您想要使用 c + + 核心指導方針檢查分析，並開啟其內容的檔案。
6.  選擇**C / C + + \Command 列選項**並加入`/analyze:plugin EspXEngine.dll`
7.  停用的先行編譯標頭 (**C / C + + 標頭 \Precompiled**)。 這是必要的因為擴充功能引擎可能會嘗試從先行編譯標頭讀取其內部的資訊，後者以編譯專案的預設選項，則將無法相容。
8.  重建專案。 常見的 PREFast 檢查應該執行的所有檔案。 因為預設不啟用 c + + 核心指導方針檢查程式，它應該只執行上已設定為使用它的檔案。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>如何使用 Visual Studio 外部的 c + + 核心指導方針檢查
您可以使用 c + + 核心指導方針檢查自動化組建中。

### <a name="msbuild"></a>MSBuild
 原生程式碼分析檢查程式 (PREfast) 已整合到自訂的目標檔案的 MSBuild 環境。 您可以使用專案屬性來啟用它，並加入 c + + 核心指導方針檢查程式 （此作業取決於 PREfast）：

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
請確認您新增的 Microsoft.Cpp.targets 檔案匯入之前，這些屬性。 您可以選擇特定的規則集或建立自訂規則集，或使用預設規則集合，包括其他 PREfast 檢查。

您也可以使用相同的方法為只在指定的檔案上執行 c + + 核心檢查[稍早所述](#coreckeck_per_file)，但是使用 MSBuild 檔案。 環境變數可以透過設定`BuildMacro`項目：

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
如果您使用不依賴 MSBuild 的建置系統仍然可以執行檢查，但必須先熟悉一些內部項目 （這不保證在未來支援） 的程式碼分析引擎設定。

您必須設定幾個環境變數，並使用適當的命令列選項的編譯器。 最好是 「 Native Tools 命令提示字元 」 環境下工作，以便您不必來搜尋特定編譯器的路徑，包含目錄等。

1.  **環境變數**
  - `set esp.extensions=cppcorecheck.dll`這會告訴引擎載入 c + + 核心指導方針模組。
  - `set esp.annotationbuildlevel=ignore`這會停用邏輯會處理 SAL 註釋。 註解不會影響程式碼分析，在 c + + 核心指導方針檢查程式，但其處理花費的時間 （有時候很多時間）。 選用但強烈建議使用此設定。
  - `set caexcludepath=%include%`我們強烈建議您停用警告發生時引發標準標頭。 您可以加入更多的路徑，例如您的專案中的通用標頭的路徑。
2.  **命令列選項**
  - `/analyze`啟用程式碼分析 (分析 / 考慮也使用： 只和 /analyze: quiet)。
  - `/analyze:plugin EspXEngine.dll`此選項會將程式碼分析擴充引擎載入 PREfast。 此引擎，接著載入 c + + 核心指導方針檢查程式。



## <a name="use-the-guideline-support-library"></a>使用指導方針支援程式庫  
 導線支援程式庫被設計來協助您遵守核心。 GSL 包含可讓您以更安全的替代項目取代出錯建構的定義。 例如，您可以取代`T*, length`組參數與`span<T>`型別。 GSL 位於[http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl)。 程式庫是開放原始碼，因此您可以檢視的來源、 註解，或 「 參與 」。 您可以在找到專案[https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)。

 ## <a name="vs2015_corecheck"></a>在 Visual Studio 2015 的專案中使用 c + + 核心檢查指導方針  
  如果您使用 Visual Studio 2015，預設不會安裝 c + + 核心檢查的程式碼分析規則集。 您必須執行一些額外的步驟，才能啟用 Visual Studio 2015 中的 c + + 核心檢查程式碼分析工具。 Microsoft 透過支援的 Visual Studio 2015 的專案使用 Nuget 封裝。 封裝名為 Microsoft.CppCoreCheck，且可在[http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck)。 此套件需要有至少安裝 Visual Studio 2015 Update 1。  
  
 套件也會安裝為相依性，僅限標頭導線支援程式庫 (GSL) 另一個封裝。 GSL 也會提供在 GitHub 上[https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)。  

 由於載入程式碼分析規則的方式，您必須安裝 Microsoft.CppCoreCheck NuGet 封裝到您想要在 Visual Studio 2015 中檢查每個 c + + 專案。  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>若要將 Microsoft.CppCoreCheck 封裝加入至 Visual Studio 2015 中的專案  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下您想要將此封裝加入方案中開啟您專案的內容功能表。 選擇**管理 NuGet 封裝**開啟**NuGet 套件管理員**。  
  
2.  在**NuGet 套件管理員**視窗中，搜尋 Microsoft.CppCoreCheck。  
  
     ![Nuget 套件管理員 視窗會顯示 CppCoreCheck 封裝](../code-quality/media/cppcorecheck_nuget_window.PNG "CPPCoreCheck_Nuget_Window")  
  
3.  選取 Microsoft.CppCoreCheck 封裝，然後選擇**安裝**按鈕，將規則加入至您的專案。  
  
 NuGet 封裝將其他的 MSBuild.targets 檔案加入專案時啟用程式碼分析您的專案上叫用。 這個.targets 檔案會將 c + + 核心檢查規則做為額外的擴充加入至 Visual Studio 程式碼分析工具。 安裝封裝時，您可以使用 [屬性頁] 對話方塊啟用或停用發行和實驗性規則。  
  
