---
title: 工作批次處理中的項目中繼資料 | Microsoft Docs
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
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c117f6864aadd7c981aa2b89302c06ccfd6c9768
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923780"
---
# <a name="item-metadata-in-task-batching"></a>工作批次處理中的項目中繼資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 能夠根據項目中繼資料，將項目清單分割成不同的類別或批次，然後使用每個批次一次執行一個工作。 要確切了解哪個批次要傳遞哪些項目，可能會相當混亂。 本主題涵蓋下列與批次處理相關的常見案例。  
  
- 將項目清單分割成批次  
  
- 將數個項目清單分割成批次  
  
- 一次批次處理一個項目  
  
- 篩選項目清單  
  
  如需有關使用 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 來進行批次處理的詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。  
  
## <a name="dividing-an-item-list-into-batches"></a>將項目清單分割成批次  
 批次處理可讓您根據項目中繼資料，將項目清單分割成不同的批次，然後將每個批次個別傳遞給工作。 這適用於建置附屬組件。  
  
 下列範例示範如何根據項目中繼資料，將項目清單分割成批次。 `ExampColl` 項目清單會根據 `Number` 項目中繼資料分割成三個批次。 `Text` 屬性中的 `%(ExampColl.Number)` 會通知 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 應該執行批次處理。 `ExampColl` 項目清單會根據 `Number` 中繼資料分割成三個批次，而系統會將每個批次個別傳遞給工作。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Message Task](../msbuild/message-task.md) 工作顯示下列資訊：  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>將數個項目清單分割成批次  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 可根據相同的中繼資料將數個項目清單分割成批次。 這可讓您輕鬆將不同的項目清單分割成批次，以建置多個組件。 例如，您可以將 .cs 檔案的項目清單分割成應用程式批次和組件批次，以及將資源檔案的項目清單分割成應用程式批次和組件批次。 接著，您可以使用批次處理將這些項目清單傳遞給一個工作，然後建置應用程式和組件。  
  
> [!NOTE]
>  如果要傳遞給工作的項目清單未包含任何具有所參考中繼資料的項目，系統就會將該項目清單中的每個項目都傳遞給每個批次。  
  
 下列範例示範如何根據項目中繼資料，將多個項目清單分割成批次。 `ExampColl` 和 `ExampColl2` 項目清單會分別根據 `Number` 項目中繼資料分割成三個批次。 `Text` 屬性中的 `%(Number)` 會通知 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 應該執行批次處理。 `ExampColl` 和 `ExampColl2` 項目清單會根據 `Number` 中繼資料分割成三個批次，而系統會將每個批次個別傳遞給工作。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [Message Task](../msbuild/message-task.md) 工作顯示下列資訊：  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>一次批次處理一個項目  
 在於建立每個項目時指派給項目的已知項目中繼資料上，也可以執行批次處理。 這可確保集合中的每個項目都具有相同的中繼資料可用於批次處理。 每個項目的 `Identity` 中繼資料值都是唯一的，可用來將項目清單中的每個項目分割成個別的批次。 如需已知項目中繼資料的完整清單，請參閱[已知的項目中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。  
  
 下列範例示範如何以一次一個的方式，批次處理項目清單中的每個項目。 由於每個項目的 `Identity` 中繼資料值是唯一的，因此 `ExampColl` 項目清單會分割成六個批次，每個批次包含項目清單的一個項目。 `Text` 屬性中的 `%(Identity)` 會通知 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 應該執行批次處理。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Message Task](../msbuild/message-task.md) 工作顯示下列資訊：  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>篩選項目清單  
 批次處理可用來先篩除項目清單中的特定項目，再將其傳遞給工作。 例如，篩選 `Extension` 已知項目中繼資料值可讓您只在具有特定副檔名的檔案上執行工作。  
  
 下列範例示範如何根據項目中繼資料，將項目清單分割成批次，然後在將這些批次傳遞給工作時，進行篩選。 `ExampColl` 項目清單會根據 `Number` 項目中繼資料分割成三個批次。 工作的 `Condition` 屬性指定只將 `Number` 項目中繼資料值為 `2` 的批次傳遞給工作  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [Message Task](../msbuild/message-task.md) 工作顯示下列資訊：  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>另請參閱  
 [已知的項目中繼資料](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item 元素 (MSBuild)](../msbuild/item-element-msbuild.md)   
 [ItemMetadata 元素 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [批次處理](../msbuild/msbuild-batching.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)



