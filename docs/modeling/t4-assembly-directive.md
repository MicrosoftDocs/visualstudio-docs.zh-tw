---
title: "T4 組件指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: "4"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 458fc4b2f96480c1f41efd8b80050fd0911b3e85
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="t4-assembly-directive"></a>T4 組件指示詞
在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設計階段文字範本中，`assembly` 指示詞會載入組件，因此範本程式碼可以使用它的類型。 這種效果類似在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中加入組件參考。  
  
 撰寫文字範本的一般概觀，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
> [!NOTE]
>  在執行階段 (前置處理過的) 文字範本中，不需要 `assembly` 指示詞。 相反地，將必要的組件，加入**參考**的您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。  
  
## <a name="using-the-assembly-directive"></a>使用組件指示詞  
 指示詞的語法如下：  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 組件名稱應該是下列其中一個：  
  
-   GAC 中組件的強式名稱，例如 `System.Xml.dll`。 您也可以使用完整格式，例如 `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`。 如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName>。  
  
-   組件的絕對路徑  
  
 `$(variableName)` 語法可用來參考 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 變數 (例如 `$(SolutionDir)`)，而 `%VariableName%` 可用來參考環境變數。 例如：  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 assembly 指示詞在前置處理過的文字範本中無效。 相反地，加入必要的參考，在**參考**區段您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## <a name="standard-assemblies"></a>標準組件  
 下列組件會自動載入，因此您不需要為它們撰寫 assembly 指示詞：  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 如果使用自訂指示詞，指示詞處理器可能會載入額外的組件。 例如，如果為特定領域語言 (DSL) 撰寫範本，就不需要為下列組件撰寫 assembly 指示詞：  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   包含 DSL 的組件。  
  
##  <a name="msbuild"></a>使用 MSBuild 和 Visual Studio 中的專案屬性  
 Visual Studio 巨集，例如 $ （solutiondir） 不在 MSBuild 中運作。 如果想要轉換組建電腦中的範本，您必須改用專案屬性。  
  
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
 [T4 包含指示詞](../modeling/t4-include-directive.md)