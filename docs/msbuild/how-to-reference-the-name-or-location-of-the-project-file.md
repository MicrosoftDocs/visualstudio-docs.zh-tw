---
title: HOW TO：參考專案檔的名稱或位置 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ce03be9eb9d1fa4926eb1100f9a2aad5612a61d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906029"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>HOW TO：參考專案檔的名稱或位置
您可以在專案檔中使用專案的名稱或位置，而不需建立自己的屬性。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供保留的屬性，來參考專案檔的名稱和其他專案相關的屬性。 如需保留屬性的詳細資訊，請參閱 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。  
  
## <a name="use-the-project-properties"></a>使用專案屬性
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供一些保留的屬性，讓您不必每次定義就能在專案檔中加以使用。 例如，保留的屬性 `MSBuildProjectName` 提供專案檔名的參考。 保留的屬性 `MSBuildProjectDirectory` 提供專案檔案位置的參考。
  
#### <a name="to-use-the-project-properties"></a>使用專案屬性
  
- 使用 $() 標記法來參考專案檔中的屬性，就像您使用其他屬性一樣。 例如：  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  使用保留屬性的一個優點是，會自動併入對專案檔名所做的任何變更。 當您下一次建置專案時，輸出檔將具備新名稱，而您不需採取任何進一步動作。  
  
> [!NOTE]
>  您無法在專案檔中重新定義保留的屬性。  
  
## <a name="example"></a>範例  
 下列範例專案檔會參考專案名稱做為保留的屬性，來指定輸出的名稱。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
     </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>範例
 下列範例專案檔使用 `MSBuildProjectDirectory` 保留屬性，在專案檔案位置中建立檔案的完整路徑。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
[MSBuild](../msbuild/msbuild.md)  
[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
