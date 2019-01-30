---
title: HOW TO：清除組建 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dab142315a7d243caf6604c5f2745244ff166e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027928"
---
# <a name="how-to-clean-a-build"></a>HOW TO：清除組建
當您清除組建時，會刪除所有中繼和輸出檔案，只留下專案檔和元件檔案。 從專案和元件檔案中，接著可以建置新的中繼和輸出檔案執行個體。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所提供的一般工作程式庫包含 [Exec](../msbuild/exec-task.md) 工作，讓您可用來執行系統命令。 如需工作程式庫的詳細資訊，請參閱[工作參考](../msbuild/msbuild-task-reference.md)。  
  
## <a name="create-a-directory-for-output-items"></a>建立輸出項目的目錄  
 根據預設，編譯專案時所建立的 *.exe* 檔案位於與專案和來源檔案相同的目錄中。 不過，一般而言，會在不同的目錄中建立輸出項目。  
  
#### <a name="to-create-a-directory-for-output-items"></a>建立輸出項目的目錄  
  
1.  使用 `Property` 項目來定義目錄的位置和名稱。 例如，在包含專案和來源檔案的目錄中，建立名為 *BuiltApp* 的目錄：  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  如果目錄不存在，請使用 [MakeDir](../msbuild/makedir-task.md) 工作來建立目錄。 例如：  
  
     ```xml
     <MakeDir Directories = "$(builtdir)"  
      Condition = "!Exists('$(builtdir)')" />
     ```
  
## <a name="remove-the-output-items"></a>移除輸出項目  
 建立新的中繼和輸出檔案執行個體之前，您可能想要清除所有先前的中繼和輸出檔案執行個體。 使用 [RemoveDir](../msbuild/removedir-task.md) 工作，以從磁碟中刪除目錄以及其所含的所有檔案和目錄。  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>移除目錄中所含的目錄和所有檔案  
  
-   使用 `RemoveDir` 工作，以移除目錄。 例如：  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>範例  
 下列程式碼範例專案包含新的目標 `Clean`，以使用 `RemoveDir` 工作來刪除目錄以及其中所含的所有檔案和目錄。 在此範例中，`Compile` 目標也會為要在清除組建時刪除的輸出項目建立個別目錄。  
  
 `Compile` 定義為預設目標，因此除非您指定不同的目標，否則都會自動予以使用。 您要使用命令列參數 **-target** 指定不同的目標。 例如：  
  
 `msbuild <file name>.proj -target:Clean`  
  
 **-target** 參數可以縮短為 **-t**，而且可以指定多個目標。 例如，若要依序使用目標 `Clean` 和目標 `Compile`，請鍵入：  
  
 `msbuild <file name>.proj -t:Clean;Compile`  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Exec 工作](../msbuild/exec-task.md)   
 [MakeDir 工作](../msbuild/makedir-task.md)   
 [RemoveDir 工作](../msbuild/removedir-task.md)   
 [Csc 工作](../msbuild/csc-task.md)   
 [目標](../msbuild/msbuild-targets.md)