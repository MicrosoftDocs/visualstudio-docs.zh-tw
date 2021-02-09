---
title: T4 組件指示詞
description: 瞭解在 Visual Studio 的設計階段文字模板中，assembly 指示詞會載入元件，讓您的範本程式碼可以使用其類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d214764e8067e1165eeacc044bddc1994230562
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899677"
---
# <a name="t4-assembly-directive"></a>T4 組件指示詞

在 Visual Studio 的設計階段文字模板中， `assembly` 指示詞會載入元件，讓您的範本程式碼可以使用其類型。 效果類似于在 Visual Studio 專案中加入元件參考。

 如需撰寫文字模板的一般總覽，請參閱 [撰寫 T4 文字模板](../modeling/writing-a-t4-text-template.md)。

> [!NOTE]
> 在執行階段 (前置處理過的) 文字範本中，不需要 `assembly` 指示詞。 相反地，請將必要的元件加入至 Visual Studio 專案的 **參考** 。

## <a name="using-the-assembly-directive"></a>使用組件指示詞
 指示詞的語法如下：

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 組件名稱應該是下列其中一個：

- GAC 中組件的強式名稱，例如 `System.Xml.dll`。 您也可以使用完整格式，例如 `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`。 如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName>。

- 組件的絕對路徑

  您可以使用 `$(variableName)` 語法來參考 Visual Studio 變數（例如 `$(SolutionDir)` ），以及 `%VariableName%` 參考環境變數。 例如：

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 assembly 指示詞在前置處理過的文字範本中無效。 相反地，請將必要的參考包含在 Visual Studio 專案的 [ **參考** ] 區段中。 如需詳細資訊，請參閱 [使用 T4 文字模板的執行時間文字產生](../modeling/run-time-text-generation-with-t4-text-templates.md)。

## <a name="standard-assemblies"></a>標準組件
 下列組件會自動載入，因此您不需要為它們撰寫 assembly 指示詞：

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  如果使用自訂指示詞，指示詞處理器可能會載入額外的組件。 例如，如果為特定領域語言 (DSL) 撰寫範本，就不需要為下列組件撰寫 assembly 指示詞：

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- 包含 DSL 的組件。

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> 在 MSBuild 和 Visual Studio 中使用專案屬性
 Visual Studio 的宏（例如 $ (SolutionDir) 無法在 MSBuild 中運作）。 如果想要轉換組建電腦中的範本，您必須改用專案屬性。

 編輯您的 .csproj 或 .vbproj 檔案以定義專案屬性。 這個範例會定義名為 `myLibFolder` 的屬性：

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

 現在您可以在文字範本中使用專案屬性，該屬性在 Visual Studio 和 MSBuild 中會正確轉換：

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>另請參閱

- [T4 包含指示詞](../modeling/t4-include-directive.md)
