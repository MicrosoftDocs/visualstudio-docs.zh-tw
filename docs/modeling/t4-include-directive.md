---
title: T4 包含指示詞
description: '瞭解在 Visual Studio 的文字模板中，您可以使用 < # # > 指示詞，來包含另一個檔案中的文字 @include 。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 825beee156c3de0e29e561817663c0f7731840dc
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363649"
---
# <a name="t4-include-directive"></a>T4 包含指示詞

在 Visual Studio 的文字模板中，您可以使用指示詞來包含另一個檔案中的文字 `<#@include#>` 。 您可以將 `include` 指示詞放在文字範本中第一個 `<#+ ... #>` 類別功能區塊之前的任何位置。 被納入的檔案也包含 `include` 指示詞和其他指示詞。 如此可讓您在範本之間共用範本程式碼和重複使用文字。

## <a name="using-include-directives"></a>使用包含指示詞

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` 可以是絕對或相對於目前的範本檔案。

   此外，特定的 Visual Studio 延伸模組可以指定自己的目錄來搜尋 include 檔。 例如，當您安裝視覺效果和模型 SDK (DSL Tools) 時，會將下列資料夾新增至 include 清單： `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` 。

   這些額外的 Include 資料夾可能相依於納入的檔案其副檔名。 例如，只有當納入的檔案其副檔名為 `.tt` 時才能使用 DSL 工具的 Include 資料夾

- `filePath` 可以包含以 "%" 分隔的環境變數。 例如：

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- 包含檔案的名稱不需要使用 `".tt"` 副檔名。

   您可以使用其他副檔名 (例如 `".t4"`) 做為包含檔案的副檔名。 這是因為當您將檔案加入 `.tt` 至專案時，Visual Studio 會自動將其 **自訂工具** 屬性設為 `TextTemplatingFileGenerator` 。 您通常不希望被納入的檔案進行個別轉換。

   另一方面，您應該留意副檔名在某些情況下會影響其他要搜尋 Include 檔的資料夾。 被納入的檔案包含其他檔案時，這一點可能十分重要。

- 處理所加入的內容時，幾乎可以將此內容當做是進行加入之文字範本的一部分來處理。 而且，即使 `<#+...#>` 指示詞後面有一般文字或標準控制區塊，您都可以納入包含類別功能區塊 `include` 的檔案。

- 使用 `once="true"` 確保範本只包含一次，即使是從多個其他 include 檔案叫用也一樣。

   這項功能可讓您輕鬆地建立可重複使用之 T4 程式碼片段的程式庫，您可以將它包含在其中，而不需要擔心其他程式碼片段已包含這些程式碼片段。  例如，假設您有一個非常精細的程式碼片段程式庫，可處理範本處理和 c # 產生。  然後，這些公用程式會使用這些公用程式，例如產生例外狀況，然後您可以從任何其他應用程式特定的範本使用這些公用程式。 如果您繪製相依性圖形，就會看到某些程式碼片段會被包含數次。 但 `once` 參數會阻止後續的包含項。

  **MyTextTemplate.tt：**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4：**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4：**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **產生的檔案，MyTextTemplate.txt：**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> 在 MSBuild 和 Visual Studio 中使用專案屬性
 雖然您可以在 include 指示詞中使用 Visual Studio 宏（例如 $ (SolutionDir) ），但它們在 MSBuild 中無法運作。 如果想要轉換組建電腦中的範本，您必須改用專案屬性。

 編輯您的 .csproj 或 .vbproj 檔案以定義專案屬性。 這個範例會定義名為 `myIncludeFolder` 的屬性：

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 現在您可以在文字範本中使用專案屬性，該屬性在 Visual Studio 和 MSBuild 中會正確轉換：

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
