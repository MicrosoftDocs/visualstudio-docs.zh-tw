---
title: 建置流程中的程式碼產生
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4d26c0b464341bee7bce0b46bfdbcc89e0248a81
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163125"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>在組建進程中叫用文字轉換

[文字轉換](../modeling/code-generation-and-t4-text-templates.md)可以在 Visual Studio 方案的[組建](/azure/devops/pipelines/index)程式中叫用。 有的建置工作會針對文字轉換進行特製化。 T4 建置工作會執行設計階段的文字範本，也會編譯執行階段 (前置處理過後) 的文字範本。

根據不同的建置引擎，建置工作可執行的動作會有些差異。 當您在 Visual Studio 中建立方案時，如果已設定[hostspecific = "true"](../modeling/t4-template-directive.md)屬性，文字模板就可以存取 Visual Studio API （EnvDTE）。 但是當您從命令列建立解決方案，或透過 Visual Studio 起始伺服器組建時，也不會發生這種情況。 在這些情況下，會由 MSBuild 執行組建，並會使用不同的 T4 主機。 這表示當您使用 MSBuild 建立文字模板時，您無法以相同的方式存取專案檔名稱之類的事項。 不過，您可以[使用組建參數，將環境資訊傳遞至文字模板和](#parameters)指示詞處理器。

## <a name="buildserver"></a>設定您的電腦

若要在您的開發電腦上啟用組建工作，請安裝適用于 Visual Studio 的模型 SDK。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

如果[您的組建伺服器](/azure/devops/pipelines/agents/agents)是在未安裝 Visual Studio 的電腦上執行，請從開發電腦將下列檔案複製到組建電腦：

- % ProgramFiles （x86）% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - VisualStudio. TextTemplating. 15.0 .dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles （x86）% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4。0

  - VisualStudio. TextTemplating. 15.0 .dll
  - VisualStudio. TextTemplating. 15.0 .dll
  - VisualStudio. TextTemplating. .Vshost.exe. 15.0 .dll

- % ProgramFiles （x86）% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - VisualStudio. TextTemplating. 15.0 .dll
  
> [!TIP]
> 如果您在組建伺服器上執行 TextTemplating 組建目標時，CodeAnalysis 方法的 `MissingMethodException`，請確定 Roslyn 元件位於與組建可執行檔相同的目錄中名為*Roslyn*的目錄中（例如， *msbuild.exe*）。

## <a name="edit-the-project-file"></a>編輯專案檔

編輯您的專案檔以設定 MSBuild 中的某些功能，例如匯入文字轉換目標。

在**方案總管**中，從專案的右鍵功能表選擇 **[** 卸載]。 如此可讓您在 XML 編輯器中編輯 .csproj 或 .vbproj 檔案。 當您完成編輯時，請選擇 [**重載**]。

## <a name="import-the-text-transformation-targets"></a>匯入文字轉換目標

在 .vbproj 或 .csproj 檔案中，尋找如下所列的程式行：

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\-或-

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

在那一行之後，插入文字範本化匯入：

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>轉換組建中的範本

其中具有可輸入至專案檔以控制轉換工作的一些屬性：

- 在每個組建的開始處執行轉換工作：

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- 覆寫唯讀的檔案，例如，因為它們未簽出：

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- 每次轉換每一個範本：

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     根據預設，T4 MSBuild 工作會重新產生超過下列時間的輸出檔案：
     
     - 其範本檔案
     - 包含的任何檔案
     - 範本先前已讀取的任何檔案，或其使用的指示詞處理器
     
     這是比 Visual Studio 中的 [**轉換所有範本**] 命令所使用的更強大的相依性測試，其只會比較範本和輸出檔案的日期。

若在專案中僅執行文字轉換，請叫用 TransformAll 工作：

`msbuild myProject.csproj /t:TransformAll`

轉換特定文字範本：

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

您可以在 TransformFile 中使用萬用字元：

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>原始檔控制

與原始檔控制系統的特定內建整合並未提供。 不過，您可以新增自己的延伸模組，例如簽出和簽入產生的檔案。 根據預設，文字轉換工作會避免覆寫標示為唯讀的檔案。 當遇到這類檔案時，Visual Studio 錯誤清單會記錄錯誤，而且工作會失敗。

若要指定必須覆寫唯讀檔案，請插入以下屬性：

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

除非您自訂後處理步驟，否則當覆寫檔案時，會將警告記錄在錯誤清單中。

## <a name="customize-the-build-process"></a>自訂群組建進程

文字轉換會在建置程序的其他工作之前運作。 藉由設定 `$(BeforeTransform)` 和 `$(AfterTransform)` 屬性，您可以定義轉換之前和之後叫用的工作：

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

在 `AfterTransform` 中，您可以參考檔案清單：

- GeneratedFiles：流程所寫入之檔案的清單。 對於已覆蓋現有唯讀檔案的檔案，`%(GeneratedFiles.ReadOnlyFileOverwritten)` 將會是 true。 您可以從原始檔控制中簽出這些檔案。

- NonGeneratedFiles：不會遭到覆寫之唯讀檔案的清單。

例如，您可以定義工作以檢查 GeneratedFiles。

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath 和 OutputFileName

這些屬性只能由 MSBuild 使用。 它們並不會影響在 Visual Studio 中產生的程式碼。 它們會將產生的輸出檔重新導向至不同資料夾或檔案。 目標資料夾必須已經存在。

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

要重新導向的實用資料夾是 `$(IntermediateOutputPath)`。

如果您指定輸出檔案名，它的優先順序會高於範本中 output 指示詞所指定的副檔名。

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

如果您也要使用 [**全部轉換**] 或 [執行單一檔案產生器] 來轉換 Visual Studio 內的範本，則不建議指定 OutputFileName 或 OutputFilePath。 根據您觸發轉換的方式而定，您會得到不同的檔案路徑。 這可能會造成混淆。

## <a name="add-reference-and-include-paths"></a>新增參考和包含路徑

主機具有搜尋範本中所參考組件的預設路徑集合。 加入至這個集合：

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

若要設定搜尋包含檔案的資料夾，請提供以分號分隔的清單。 通常會加入至現有的資料夾清單。

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a>將組建內容資料傳遞至範本

您可以在專案檔中設定參數值。 例如，您可以傳遞[組建](../msbuild/msbuild-properties.md)屬性和[環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md)：

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

在文字範本內，在範本指示詞中設定 `hostspecific`。 使用[參數](../modeling/t4-parameter-directive.md)指示詞取得值：

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

在指示詞處理器中，您可以呼叫[ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))：

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> 只有在您使用 MSBuild 時，`ResolveParameterValue` 才會從 `T4ParameterValues` 取得資料。 當您使用 Visual Studio 轉換範本時，參數會有預設值。

## <a name="msbuild"></a>在 assembly 和 include 指示詞中使用專案屬性

Visual Studio 宏（例如 **$ （SolutionDir））** 在 MSBuild 中無法使用。 您可以改用專案屬性。

編輯您*的 .csproj*或 *. vbproj*檔案，以定義專案屬性。 這個範例會定義名為**myLibFolder**的屬性：

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

您現在可以在 assembly 和 include 指示詞中使用專案屬性：

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

這些指示詞會從 MSBuild 和 Visual Studio 裝載中的 T4parameterValues 取得值。

## <a name="q--a"></a>問與答

@no__t 0Why 是否要轉換組建伺服器中的範本？我在簽入我的程式碼之前，已轉換 Visual Studio 中的範本。 **

如果您更新包含的檔案或範本所讀取的其他檔案，Visual Studio 不會自動轉換檔案。 將範本轉換為組建的一部分，可確保所有專案都是最新的。

**轉換文字模板有哪些其他選項？**

- [TextTransform 公用程式](../modeling/generating-files-with-the-texttransform-utility.md)可用於命令腳本中。 在大部分的情況下，使用 MSBuild 會比較容易。

- 叫[用 Visual Studio 延伸模組中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。

- [設計階段的文字模板](../modeling/design-time-code-generation-by-using-t4-text-templates.md)會由 Visual Studio 轉換。

- [執行時間文字模板](../modeling/run-time-text-generation-with-t4-text-templates.md)會在應用程式的執行時間進行轉換。

## <a name="see-also"></a>另請參閱

::: moniker range="vs-2017"

- @No__t-0 的 T4 MSbuild 範本中有絕佳的指引

::: moniker-end

::: moniker range=">=vs-2019"

- @No__t-0 的 T4 MSbuild 範本中有絕佳的指引

::: moniker-end

- [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)
