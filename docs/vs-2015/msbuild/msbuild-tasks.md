---
title: MSBuild 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 611bc5c0fbb81d38aa10561d8603ef281a51d9a1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54788685"
---
# <a name="msbuild-tasks"></a>MSBuild 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
組建平台必須能夠在建置程序期間執行任意數目的動作。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會使用「工作」來執行這些動作。 工作是 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 用來執行不可部分完成之建置作業的可執行程式碼單元。  
  
## <a name="task-logic"></a>工作邏輯  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML 專案檔格式無法完全獨立執行建置作業，因此，必須在專案檔以外的地方實作工作邏輯。  
  
 工作的執行邏輯會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework> 命名空間中所定義的 <xref:Microsoft.Build.Framework.ITask> 介面。  
  
 工作類別也會定義可供專案檔中的工作使用的輸入和輸出參數。 由工作類別公開的所有公用、可設定、非靜態且非抽象的屬性都可在專案檔中加以存取，方法是在 [Task](../msbuild/task-element-msbuild.md) 項目上放置具有相同名稱的對應屬性。  
  
 若要撰寫自己的工作，請編寫可實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類別。 如需詳細資訊，請參閱[工作撰寫](../msbuild/task-writing.md)。  
  
## <a name="executing-a-task-from-a-project-file"></a>從專案檔執行工作  
 在執行專案檔中的工作之前，您必須先使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目，將實作工作之組件中的類型對應到工作名稱。 這讓 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 知道，如果它在您的專案檔中找到工作，應該到何處尋找該工作的執行邏輯。  
  
 若要執行 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔中的工作，請使用工作名稱建立項目以做為 `Target` 項目的子系。 如果工作接受參數，則會傳遞這些參數以做為項目的屬性。  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 項目清單和屬性都可用來做為參數。 例如，下列程式碼會呼叫 `MakeDir` 工作，並設定 `MakeDir` 物件的 `Directories` 屬性值等於前一個範例中所宣告的 `BuildDir` 屬性值。  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 工作也可以將資訊傳回專案檔，資訊可儲存於項目或屬性中，以供稍後使用。 例如，下列程式碼會呼叫 `Copy` 工作，並將來自 `CopiedFiles` 輸出屬性的資訊儲存於 `SuccessfullyCopiedFiles` 項目清單中。  
  
```  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>包含的工作  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 隨附許多工作，例如，用於複製檔案的 [Copy](../msbuild/copy-task.md)、用於建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及用於編譯 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。 如需可用工作的完整清單和用法資訊，請參閱[工作參考](../msbuild/msbuild-task-reference.md)。  
  
## <a name="overridden-tasks"></a>覆寫的工作  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會在數個位置中尋找工作。 第一個位置是在儲存於 .NET Framework 目錄中副檔名為 .OverrideTasks 的檔案中。 這些檔案中的工作會覆寫任何其他具有相同名稱的工作，包括專案檔中的工作。 第二個位置是在 .NET Framework 目錄中副檔名為 .Tasks 的檔案中。 如果在這兩個位置中找不到工作，就會使用專案檔中的工作。  
  
## <a name="see-also"></a>請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md)   
 [工作撰寫](../msbuild/task-writing.md)   
 [內嵌工作](../msbuild/msbuild-inline-tasks.md)
