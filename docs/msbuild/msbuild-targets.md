---
title: MSBuild 目標 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f6ae74ed310da6f937dcadf168630102c004877
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081435"
---
# <a name="msbuild-targets"></a>MSBuild 目標
依特定順序將目標設為群組工作，並允許將建置處理序分成較小的單位。 例如，一個目標可能會刪除輸出目錄中的所有檔案來準備進行建置，而另一個目標會編譯專案的輸入，並將它們放在空目錄中。 如需工作的詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。  
  
## <a name="declaring-targets-in-the-project-file"></a>在專案檔中宣告目標  
 在專案檔中，目標是使用 [Target](../msbuild/target-element-msbuild.md) 項目所宣告。 例如，下列 XML 會建立名為 Construct 的目標，其接著會呼叫具有 Compile 項目類型的 Csc 工作。  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 與 MSBuild 屬性相同，可以重新定義目標。 例如，套用至物件的  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 如果執行 AfterBuild，則只會顯示「第二次出現」。  
  
## <a name="target-build-order"></a>目標組建順序  
 如果某一個目標的輸入相依於另一個目標的輸出，則必須排序目標。 有幾種方式可指定目標的執行順序。  
  
-   初始目標  
  
-   預設目標  
  
-   第一個目標  
  
-   目標相依性  
  
-   `BeforeTargets` 和 `AfterTargets` (MSBuild 4.0)  

目標絕對不會在單一建置期間執行兩次，即使組建中的後續目標相依於它也一樣。 執行目標之後，它對組建而言就已功成身退了。  

如需目標建置順序的詳細資料和詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。  

## <a name="target-batching"></a>目標批次處理  
目標項目可能有 `Outputs` 屬性以 %(\<中繼資料>) 形式指定中繼資料。 如果是這樣，MSBuild 會為每個唯一的中繼資料值執行一次目標，並分組或「批次處理」具有該中繼資料值的項目。 例如，套用至物件的  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 依其 RequiredTargetFramework 中繼資料，批次處理 Reference 項目。 目標的輸出如下所示：  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 目標批次處理很少用於真實的組建。 工作批次處理較為常見。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。  
  
## <a name="incremental-builds"></a>累加建置  
 累加組建是已最佳化的建置，因此不會執行輸出檔案與其相關對應輸入檔案為最新的目標。 目標項目可能有 `Inputs` 和 `Outputs` 屬性，並指出目標預期作為輸入的項目，以及它產生作為輸出的項目。  
  
 如果所有輸出項目都是最新的，則 MSBuild 會略過目標，這可大幅改善建置速度。 這稱為目標的累加組建。 如果只有某些檔案是最新的，則 MSBuild 會執行沒有最新項目的目標。 這稱為目標的部分累加組建。 如需詳細資訊，請參閱[累加建置](../msbuild/incremental-builds.md)。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [如何：在多個專案檔中使用相同目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)