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
ms.openlocfilehash: d790110d76a8500d127e34842c63648ce5169914
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821417"
---
# <a name="code-generation-in-a-build-process"></a>在建置流程中的程式碼產生

[文字轉換](../modeling/code-generation-and-t4-text-templates.md)可以叫用的一部分[建置程序](/azure/devops/pipelines/index)的 Visual Studio 方案。 有的建置工作會針對文字轉換進行特製化。 T4 建置工作會執行設計階段的文字範本，也會編譯執行階段 (前置處理過後) 的文字範本。

根據不同的建置引擎，建置工作可執行的動作會有些差異。 如果當您建置 Visual Studio 中的解決方案時，文字範本可以存取 Visual Studio API (EnvDTE) [hostspecific ="true"](../modeling/t4-template-directive.md)屬性設定。 但當您建置解決方案，從命令列，或當您起始透過 Visual Studio 的伺服器組建時也不會。 在這些情況下，會由 MSBuild 執行組建，並會使用不同的 T4 主機。

這表示您無法將專案檔案名稱等項目存取相同的方式建置在 MSBuild 中的文字範本時。 不過，您可以[傳遞環境資訊至文字範本和指示詞處理器，使用組建參數](#parameters)。

## <a name="buildserver"></a> 設定您的電腦

若要啟用建置工作，在您的開發電腦上，安裝 Visual Studio Modeling SDK。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

如果[您的組建伺服器](/azure/devops/pipelines/agents/agents)未安裝 Visual Studio，在電腦上的執行從開發電腦將下列檔案複製到組建電腦。 替代的最新的版本號碼 ' *'。

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.*.0.dll

  - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (數個檔案)

  - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

  - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>若要編輯專案檔

您必須編輯專案檔，才能在 MSBuild 中設定的一些功能。

在 **方案總管**，選擇**卸載**從您的專案上按一下滑鼠右鍵功能表。 如此可讓您在 XML 編輯器中編輯 .csproj 或 .vbproj 檔案。

當您完成編輯時，請選擇**重新載入**。

## <a name="import-the-text-transformation-targets"></a>匯入文字轉換目標

在 .vbproj 或 .csproj 檔案中，尋找如下所列的程式行：

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\-或-

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

在那一行之後，插入文字範本化匯入：

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">16.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>轉換在組建中的範本

其中具有可輸入至專案檔以控制轉換工作的一些屬性：

- 在每個組建的開始處執行轉換工作：

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- 覆寫唯讀的檔案，因為它們未被簽出：

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

     根據預設，如果範本檔、包含的檔案，或是所有之前已由範本、所使用指示詞處理器讀取的檔案的建立時間較晚，T4 MSBuild 工作會重新產生輸出檔。 請注意，在只比較範本和輸出檔案的日期的情況下，此相依性測試將比在 Visual Studio 中的 Transform All Templates 命令來得更為強大。

若在專案中僅執行文字轉換，請叫用 TransformAll 工作：

`msbuild myProject.csproj /t:TransformAll`

轉換特定文字範本：

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

您可以在 TransformFile 中使用萬用字元：

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>原始檔控制

與原始檔控制系統的特定內建整合並未提供。 不過，您可以加入自己的擴充功能，例如簽出和簽入產生的檔案。根據預設，文字轉換工作會避免覆寫標記為唯讀的檔案，因此，當遇到這類型檔案時，會將錯誤記錄至 Visual Studio 的錯誤清單，並中斷工作。

若要指定必須覆寫唯讀檔案，請插入以下屬性：

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

除非您自訂後置處理步驟，否則覆寫檔案時就會將警告記錄於錯誤清單中。

## <a name="customize-the-build-process"></a>自訂建置流程

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

- GeneratedFiles：流程所寫入之檔案的清單。 對於已覆寫現有唯讀檔的檔案而言，%(GeneratedFiles.ReadOnlyFileOverwritten) 將會是 true。 您可以從原始檔控制中簽出這些檔案。

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

一個可用於重新導向的資料夾為 `$(IntermediateOutputPath).`

如果您指定輸出檔名，則會優先於範本中輸出指示詞指定的副檔名。

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

您也要轉換在 VS 使用 轉換所有檔案，或執行單一檔案產生器的範本時，不建議指定 OutputFileName 和 OutputFilePath。 根據觸發轉換的方法，最後將會產生不同的檔案路徑。 這很容易混淆。

## <a name="add-reference-and-include-paths"></a>加入參考，並包含路徑

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

## <a name="parameters"></a> 將建置內容資料傳遞至範本

您可以在專案檔中設定參數值。 例如，您可以傳遞[建置](../msbuild/msbuild-properties.md)屬性並[環境變數](../msbuild/how-to-use-environment-variables-in-a-build.md):

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

在指示詞處理器中，您可以呼叫[ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> 只有在您使用 MSBuild 時，`ResolveParameterValue` 才會從 `T4ParameterValues` 取得資料。 使用 Visual Studio 轉換範本時，參數會擁有預設值。

## <a name="msbuild"></a> 使用組件中的專案屬性和 include 指示詞

Visual Studio 巨集想 **$ （solutiondir)** 在 MSBuild 中無法運作。 您可以改用專案屬性。

編輯您 *.csproj*或是 *.vbproj*檔案，以定義專案屬性。 這個範例會定義名為的屬性**myLibFolder**:

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

**為什麼要轉換組建伺服器中的範本？我已經在 Visual Studio 中的範本之前轉換在簽入我的程式碼。**

如果您更新包含的檔案或範本讀取的另一個檔案，Visual Studio 不會自動轉換檔案。 一切正在轉換範本，因為組建的一部分可確保是最新狀態。

**其他選項為何有轉換文字範本嗎？**

- [TextTransform 公用程式](../modeling/generating-files-with-the-texttransform-utility.md)可以用於命令指令碼。 在大部分情況下，它是您更輕鬆地使用 MSBuild 項目。

- [叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [設計階段文字範本](../modeling/design-time-code-generation-by-using-t4-text-templates.md)由 Visual Studio 轉換。

- [執行階段文字範本](../modeling/run-time-text-generation-with-t4-text-templates.md)轉換您的應用程式在執行階段。

## <a name="see-also"></a>另請參閱

::: moniker range="vs-2017"

- 在 T4 MSbuild 範本中沒有正確的指引 *%programfiles (x86) %\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

::: moniker range=">=vs-2019"

- 在 T4 MSbuild 範本中沒有正確的指引 *%programfiles (x86) %\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

- [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)
