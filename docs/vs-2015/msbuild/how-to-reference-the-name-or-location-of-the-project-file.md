---
title: 如何：參考專案檔的名稱或位置 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8631d10d56a35f8cf4ef6024d087bf94ec89b9d9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845728"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>如何：參考專案檔的名稱或位置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以在專案檔中使用專案的名稱或位置，而不需建立自己的屬性。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 提供保留的屬性，來參考專案檔的名稱和其他專案相關的屬性。 如需保留屬性的詳細資訊，請參閱 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)。  
  
## <a name="using-the-msbuildprojectname-property"></a>使用 MSBuildProjectName 屬性  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 提供一些保留的屬性，讓您不必每次定義就能在專案檔中加以使用。 例如，保留的屬性 `MSBuildProjectName` 提供專案檔名的參考。  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>使用 MSBuildProjectName 屬性  
  
- 使用 $() 標記法來參考專案檔中的屬性，就像您使用其他屬性一樣。 例如:   
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  使用保留屬性的一個優點是，會自動併入對專案檔名所做的任何變更。 當您下一次建置專案時，輸出檔將具備新名稱，而您不需採取任何進一步動作。  
  
> [!NOTE]
>  您無法在專案檔中重新定義保留的屬性。  
  
## <a name="example"></a>範例  
 下列範例專案檔會參考專案名稱做為保留的屬性，來指定輸出的名稱。  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
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
  
## <a name="see-also"></a>另請參閱  
[MSBuild](msbuild.md)  
 [MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)


