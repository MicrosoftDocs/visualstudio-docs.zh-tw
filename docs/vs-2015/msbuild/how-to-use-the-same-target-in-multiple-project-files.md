---
title: 如何：在多個專案檔中使用相同的目標 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ece9041d03ee8a17a4f97f8aad3971e1181edf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488752"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>如何：使用多個專案檔內相同的目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 在多個專案檔中使用相同的目標](https://docs.microsoft.com/visualstudio/msbuild/how-to-use-the-same-target-in-multiple-project-files)。  
  
  
如果您撰寫了數個 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔，您可能已發現到需要在不同的專案檔中使用相同的工作和目標。 您可以不在每個專案檔中包含這些工作或目標的完整描述，而是在一個個別的專案檔中儲存目標，然後將該專案匯入到任何其他需要使用該目標的專案中。  
  
## <a name="using-the-import-element"></a>使用匯入元素  
 使用 `Import` 元素可將一個專案檔插入到另一個專案檔中。 所要匯入的專案檔必須是有效的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔，並且包含格式正確的 XML。 `Project` 屬性會指定所匯入之專案檔的路徑。 如需有關 `Import` 元素的詳細資訊，請參閱 [Import 元素 (MSBuild)](../msbuild/import-element-msbuild.md)。  
  
#### <a name="to-import-a-project"></a>匯入專案  
  
1.  在匯入端專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。  
  
2.  使用 `Import` 元素來匯入專案。 例如:   
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  在 `Import` 元素之後，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。  
  
## <a name="order-of-evaluation"></a>評估的順序  
 當 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 到達 `Import` 元素時，會將所匯入之專案有效地插入到匯入端專案中 `Import` 元素的位置。 因此，`Import` 元素的位置會影響屬性和項目的值。 請務必了解所匯入之專案所設定的屬性和項目，以及所匯入之專案所使用的屬性和項目。  
  
 在組建專案時，會先評估所有屬性，然後才評估項目。 例如，下列 XML 定義了所匯入的專案檔 MyCommon.targets：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 下列 XML 定義了 MyApp.proj，它會匯入 MyCommon.targets：  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 在組建專案時，會顯示下列訊息：  
  
 `Name="MyCommon"`  
  
 由於會在已於 MyApp.proj 中定義 `Name` 屬性之後，才匯入專案，因此 MyCommon.targets 中 `Name` 的定義會覆寫 MyApp.proj 中的定義。 如果是在定義 Name 屬性之前就匯入專案，組建就會顯示下列訊息：  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>匯入專案時，請使用下列方法  
  
1.  在專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。  
  
2.  匯入專案。  
  
3.  在專案檔中，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範第二個程式碼範例匯入的 MyCommon.targets 檔案。 .targets 檔案會評估來自匯入端專案的屬性以設定組建。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會匯入 MyCommon.targets 檔案。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)   
 [目標](../msbuild/msbuild-targets.md)



