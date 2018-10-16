---
title: 如何：擴充 Visual Studio 建置處理序 | Microsoft Docs
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
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f318f6092c24c58399b40c7a20c967a89ca5219
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191626"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>如何：擴充 Visual Studio 建置處理序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建置處理序是由匯入至您專案檔的一系列 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .targets 檔案所定義。 可以擴充其中一個已匯入的檔案 (Microsoft.Common.targets)，以讓您在建置處理序的數個點執行自訂工作。 本主題說明您可以使用兩種方法來擴充 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建置處理序：  
  
-   覆寫 Microsoft.Common.targets 中所定義的特定預先定義目標。  
  
-   覆寫 Microsoft.Common.targets 中所定義的 "DependsOn" 屬性。  
  
## <a name="overriding-predefined-targets"></a>覆寫預先定義的目標  
 Microsoft.Common.targets 檔案包含一組預先定義的空目標，可在建置處理序的部分主要目標之前和之後呼叫。 例如，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 在主要 `CoreBuild` 目標之前呼叫 `BeforeBuild` 目標，而在 `CoreBuild` 目標之後呼叫 `AfterBuild` 目標。 Microsoft.Common.targets 中的空目標預設不會執行任何作業，但是您可以在匯入 Microsoft.Common.targets 的專案檔中定義您想要的目標，來覆寫其預設行為。 若要這麼做，您可以使用 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工作，更充分地控制建置處理序。  
  
#### <a name="to-override-a-predefined-target"></a>覆寫預先定義的目標  
  
1.  識別 Microsoft.Common.targets 中您要覆寫的預先定義目標。 如需您可安全覆寫之目標的完整清單，請參閱下表。  
  
2.  在專案檔結尾，於 `</Project>` 標記的正前方定義目標。 例如:   
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  建置專案檔。  
  
 下表顯示 Microsoft.Common.targets 中您可安全覆寫的所有目標。  
  
|目標名稱|描述|  
|-----------------|-----------------|  
|`BeforeCompile`、 `AfterCompile`|在核心編譯完成之前或之後，會執行插入至其中一個目標的工作。 大部分的自訂是在這兩個目標的其中一個中完成。|  
|`BeforeBuild`、 `AfterBuild`|在組建的任何其他項目之前或之後，將會執行其中一個目標中插入的工作。 **注意：** 在大部分專案檔結尾的註解中，已定義 `BeforeBuild` 和 `AfterBuild` 目標。 這可讓您輕鬆地將建置前和建置後事件新增至專案檔。|  
|`BeforeRebuild`、 `AfterRebuild`|在叫用核心重建功能之前或之後，執行插入至其中一個目標的工作。 Microsoft.Common.targets 中的目標執行順序是：`BeforeRebuild`、`Clean`、`Build` 和 `AfterRebuild`。|  
|`BeforeClean`、 `AfterClean`|在叫用核心清除功能之前或之後，執行插入至其中一個目標的工作。|  
|`BeforePublish`、 `AfterPublish`|在叫用核心發行功能之前或之後，執行插入至其中一個目標的工作。|  
|`BeforeResolveReference`、 `AfterResolveReferences`|在解析組件參考之前或之後，會執行插入至其中一個目標的工作。|  
|`BeforeResGen`、 `AfterResGen`|在產生資源之前或之後，會執行插入至其中一個目標的工作。|  
  
## <a name="overriding-dependson-properties"></a>覆寫 "DependsOn" 屬性  
 覆寫預先定義的目標是擴充建置處理序的簡單方法，但因為 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會循序評估目標的定義，所以沒有任何方法可防止另一個匯入您專案的專案覆寫您已覆寫的目標。 因此，例如，在匯入所有其他專案之後，專案檔中所定義的最後一個 `AfterBuild` 目標就是建置期間所使用的目標。  
  
 您可以覆寫整個 Microsoft.Common.targets 檔案之 `DependsOnTargets` 屬性中所使用的 "DependsOn" 屬性，來防止意外覆寫目標。 例如，`Build` 目標包含 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 屬性值。 請考慮：  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 這部分的 XML 指出必須先執行 `BuildDependsOn` 屬性中所指定的所有目標，才能執行 `Build` 目標。 `BuildDependsOn` 屬性定義為：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 您可以在專案檔結尾宣告名為 `BuildDependsOn` 的另一個屬性，來覆寫此屬性值。 在新屬性中包含先前的 `BuildDependsOn` 屬性，即可將新目標新增至目標清單開頭和結尾。 例如:   
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 匯入您專案檔的專案可以覆寫這些屬性，而不覆寫您進行的自訂。  
  
#### <a name="to-override-a-dependson-property"></a>覆寫 "DependsOn" 屬性  
  
1.  識別 Microsoft.Common.targets 中您要覆寫的預先定義 "DependsOn" 屬性。 如需經常覆寫的 "DependsOn" 屬性清單，請參閱下表。  
  
2.  在專案檔結尾定義另一個屬性執行個體。 在新屬性中，包含原始屬性 (例如 `$(BuildDependsOn)`)。  
  
3.  在屬性定義之前或之後，定義您的自訂目標。  
  
4.  建置專案檔。  
  
### <a name="commonly-overridden-dependson-properties"></a>經常覆寫的 "DependsOn" 屬性  
  
|屬性名稱|描述|  
|-------------------|-----------------|  
|`BuildDependsOn`|如果您想要在整個建置處理序之前或之後插入自訂目標，這是要覆寫的屬性。|  
|`CleanDependsOn`|如果您想要清除自訂建置處理序的輸出，這是要覆寫的屬性。|  
|`CompileDependsOn`|如果您想要在編譯步驟之前或之後插入自訂處理序，這是要覆寫的屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [.Targets 檔案](../msbuild/msbuild-dot-targets-files.md)



