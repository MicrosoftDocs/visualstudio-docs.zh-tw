---
title: HOW TO：在組建中使用環境變數 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78cdc8f95c5a48e8ce0491926b27f0521705e3bb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655877"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>HOW TO：在組建中使用環境變數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您建置專案時，通常需要使用專案檔或構成專案之檔案中沒有的資源來設定組建選項。 此資訊通常會儲存於環境變數中。  
  
## <a name="referencing-environment-variables"></a>參考環境變數  
 所有環境變數都可供 [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) 專案檔用來做為屬性。  
  
> [!NOTE]
>  如果專案檔包含與環境變數相同名稱之專案的明確定義，則專案檔中的屬性會覆寫環境變數的值。  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>在 MSBuild 專案中使用環境變數  
  
- 參考環境變數的方式，與您對專案檔中宣告之變數所做的相同。 例如，下列程式碼會參考 BIN_PATH 環境變數：  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  如果未設定環境變數，您可以使用 `Condition` 屬性 (Attribute) 來提供屬性 (Property) 的預設值。  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>提供屬性的預設值  
  
-   只有當屬性 (Property) 沒有任何值，才能在屬性 (Property) 上使用 `Condition` 屬性 (Attribute) 來設定值。 例如，下列程式碼只有在未設定 `ToolsPath` 環境變數時，才會將 `ToolsPath` 屬性設為 c:\tools：  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  屬性名稱是不區分大小寫的，因此 `$(ToolsPath)` 和 `$(TOOLSPATH)` 會參考相同的屬性或環境變數。  
  
## <a name="example"></a>範例  
 下列專案檔會使用環境變數來指定目錄位置。  
  
```  
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

[MSBuild](msbuild.md)

[MSBuild 屬性](../msbuild/msbuild-properties1.md)

[如何：建置使用不同的選項相同的原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
