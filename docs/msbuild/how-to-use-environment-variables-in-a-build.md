---
title: "如何：在組建中使用環境變數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 352950f52c335be52b1765a6008c26db1550a5b0
ms.contentlocale: zh-tw
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-environment-variables-in-a-build"></a>如何：在組建中使用環境變數
當您建置專案時，通常需要使用專案檔或構成專案之檔案中沒有的資源來設定組建選項。 此資訊通常會儲存於環境變數中。  
  
## <a name="referencing-environment-variables"></a>參考環境變數  
 所有環境變數都可供 [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) 專案檔用來做為屬性。  
  
> [!NOTE]
>  如果專案檔包含與環境變數相同名稱之專案的明確定義，則專案檔中的屬性會覆寫環境變數的值。  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>在 MSBuild 專案中使用環境變數  
  
-   參考環境變數的方式，與您對專案檔中宣告之變數所做的相同。 例如，下列程式碼會參考 BIN_PATH 環境變數：  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 如果未設定環境變數，您可以使用 `Condition` 屬性 (Attribute) 來提供屬性 (Property) 的預設值。  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>提供屬性的預設值  
  
-   只有當屬性 (Property) 沒有任何值，才能在屬性 (Property) 上使用 `Condition` 屬性 (Attribute) 來設定值。 例如，下列程式碼只有在未設定 `ToolsPath` 環境變數時，才會將 `ToolsPath` 屬性設為 c:\tools：  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  屬性名稱是不區分大小寫的，因此 `$(ToolsPath)` 和 `$(TOOLSPATH)` 會參考相同的屬性或環境變數。  
  
## <a name="example"></a>範例  
 下列專案檔會使用環境變數來指定目錄位置。  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [如何：使用不同選項來建置相同的原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
