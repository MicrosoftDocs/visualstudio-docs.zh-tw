---
title: "使用相依性圖表驗證程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 02c983fb7cd797be377f8821c46b2d7dc38450f9
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="validate-code-with-dependency-diagrams"></a>使用相依性圖表驗證程式碼

**最新消息**： 請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/11/30/live-dependency-validation-in-visual-studio-2017/)。

[影片： 驗證您的架構相依性，即時](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

## <a name="why-use-dependency-diagrams"></a>為何要使用相依性圖表？

若要確定程式碼不會與其設計相衝突，以驗證程式碼在 Visual Studio 中的相依性圖表。 這可協助您：  
  
-   相依性圖表上，找出您的程式碼中的相依性和相依性之間的衝突。  
  
-   尋找可能會受到建議變更所影響的相依性。  
  
     例如，您可以編輯相依性圖表，來顯示潛在的架構變更，然後驗證程式碼，以便查看受影響的相依性。  
  
-   將程式碼重構或移轉至不同設計。  
  
     在您將程式碼移至不同的架構時，請尋找需要運作的程式碼或相依性。  
  
 **需求**  
  
-   Visual Studio  
  
-   在您的 Team Foundation Build 伺服器的 Visual Studio 使用 Team Foundation Build 自動驗證程式碼  
  
-   具有相依性圖表的模型專案的方案。 此相依性圖表必須連結到您想要驗證的 Visual C#.NET 或 Visual Basic.NET 專案中的成品。 請參閱[從程式碼中建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 您可以驗證程式碼以手動方式從 Visual Studio 中開啟相依性圖表或在命令提示字元。 您也可以在執行本機組建或 Team Foundation Build 時自動驗證程式碼。 請參閱[Channel 9 影片： 設計和驗證架構使用相依性圖表](http://go.microsoft.com/fwlink/?LinkID=252073)。  
  
> [!IMPORTANT]
>  如果您要以 Team Foundation Build 執行圖層驗證，您也必須在您的組建伺服器上安裝相同版本的 Visual Studio。  
  
-   [查看項目是否支援驗證](#SupportsValidation)  
  
-   [包含其他.NET 組件和專案來進行驗證](#IncludeReferences)  
  
-   [手動驗證程式碼](#ValidateManually)  
  
-   [自動驗證程式碼](#ValidateAuto)  
  
-   [疑難排解圖層驗證問題](#TroubleshootingValidation)  
  
-   [了解並解決圖層驗證錯誤](#UnderstandingValidationErrors)  

## <a name="live-dependency-validation"></a>即時的相依性驗證

在此版本的 Visual Studio 中，相依性驗證發生在即時，錯誤會立即顯示在 Visual Studio 錯誤清單視窗。

* C# 和 Visual basic.net 支援即時驗證。 

* 若要使用即時的相依性驗證時，請啟用完整解決方案分析，請從金級列出現在 錯誤清單中開啟 選項 設定。 
 - 如果您不想看到所有架構的問題，您的方案中，您可以永久關閉此金級列。
 - 如果您未啟用完整解決方案分析，分析是基於只正在編輯的檔案。<p /> 

* 升級專案，以啟用即時驗證時，對話方塊會顯示轉換的進度。

* 更新時即時的相依性驗證的專案，NuGet 套件的版本升級為相同的所有專案，並為使用中的最高版本。 

* 加入新的相依性驗證專案觸發專案更新。 
  
##  <a name="SupportsValidation"></a>查看項目是否支援驗證  
 您可以將圖層連結到網站、Office 文件、純文字檔以及跨多個應用程式共用之專案中的檔案，不過，驗證流程不包含這些檔案。 對於連結至個別圖層之專案或組件的參考，如果這些圖層之間沒有任何相依性，則不會出現驗證錯誤。 除非程式碼使用這些參考，否則不會考量此類參考的相依性。  
  
1.  相依性圖表中，選取一或多個圖層，以滑鼠右鍵按一下您的選擇，然後按一下**檢視連結**。  
  
2.  在**圖層總管**，看看**支援驗證**資料行。 如果值為 false，則這個項目不支援驗證。  
  
##  <a name="IncludeReferences"></a>包含其他.NET 組件和專案來進行驗證  
 當您將項目拖曳到相依性圖表時，參考對應的.NET 組件或專案會自動加入至**圖層參考**模型專案中的資料夾。 這個資料夾包含組件的參考以及驗證期間分析的專案。 您可以包含其他.NET 組件和專案來進行驗證，而不用手動拖曳到相依性圖表。  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下模型專案或**圖層參考**資料夾，然後再按一下**加入參考**。  
  
2.  在**加入參考**對話方塊中，選取的組件或專案，然後按一下**確定**。  
  
##  <a name="ValidateManually"></a>手動驗證程式碼  
 如果您有已連結至方案項目開啟相依性圖表，您可以執行**驗證**從圖表的捷徑命令。 您也可以使用命令提示字元執行**msbuild**命令搭配**/p:ValidateArchitecture**自訂屬性設定為**True**。 例如，在您變更程式碼時定期執行圖層驗證，以便早期攔截相依性衝突。  
  
#### <a name="to-validate-code-from-an-open-dependency-diagram"></a>若要從開啟的相依性圖表驗證程式碼   
  
1.  以滑鼠右鍵按一下圖表介面，然後按一下**驗證架構**。  
  
    > [!NOTE]
    >  根據預設，**建置動作**相依性圖表 (.layerdiagram) 檔案的屬性設定為**驗證**以便圖表納入驗證程序中。  
  
     **錯誤清單**視窗會報告任何錯誤發生。 如需有關驗證錯誤的詳細資訊，請參閱[了解並解決圖層驗證錯誤](#UnderstandingValidationErrors)。  
  
2.  若要檢視每個錯誤的來源，請按兩下中的錯誤**錯誤清單**視窗。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可能會顯示 Code Map，而非錯誤來源。 會發生這種情況是當程式碼會具有相依性的相依性圖表中，未指定的組件，或是程式碼遺失相依性圖表所指定相依性。 請檢閱 Code Map 或程式碼，以判斷相依性是否應存在。 如需 code map 的詳細資訊，請參閱[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)。  
  
3.  若要管理錯誤，請參閱[管理驗證錯誤](#ManageErrors)。  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>若要在命令提示字元驗證程式碼  
  
1.  開啟 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示字元。  
  
2.  選擇下列其中一項：  
  
    -   若要根據方案中的特定模型專案來驗證程式碼，請使用下列自訂屬性執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]。  
  
        ```  
        msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
        ```  
  
         - 或 -  
  
         瀏覽資料夾，其中包含模型專案 (.modelproj) 檔案和相依性圖表，然後執行[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]使用下列自訂屬性：  
  
        ```  
        msbuild /p:ValidateArchitecture=true   
        ```  
  
    -   若要根據方案中的所有模型專案來驗證程式碼，請使用下列自訂屬性執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]：  
  
        ```  
        msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
        ```  
  
         - 或 -  
  
         瀏覽至方案資料夾中，其中必須包含模型專案包含相依性圖表，然後再執行[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]使用下列自訂屬性：  
  
        ```  
        msbuild /p:ValidateArchitecture=true  
        ```  
  
     發生的任何錯誤都將列出。 如需有關[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]，請參閱[MSBuild](../msbuild/msbuild.md)和[MSBuild 工作](../msbuild/msbuild-task.md)。  
  
 如需有關驗證錯誤的詳細資訊，請參閱[了解並解決圖層驗證錯誤](#UnderstandingValidationErrors)。  
  
###  <a name="ManageErrors"></a>管理驗證錯誤  
 在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您隱藏錯誤時，最好在 [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] 中記錄工作項目。  
  
> [!WARNING]
>  您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>若要針對驗證錯誤建立工作項目  
  
-   在**錯誤清單**視窗中，以滑鼠右鍵按一下錯誤，請指向**建立工作項目**，然後按一下您想要建立的工作項目類型。  
  
 使用下列工作來管理中的驗證錯誤**錯誤清單**視窗：  
  
|**若要**|**請遵循下列步驟**|  
|------------|----------------------------|  
|在驗證期間隱藏選取的錯誤|以滑鼠右鍵按一下一個或多個選取的錯誤，請指向**管理驗證錯誤**，然後按一下 **隱藏錯誤**。<br /><br /> 隱藏的錯誤會以刪除線的格式出現。 當您下一次執行驗證時，這些錯誤將不會出現。<br /><br /> 隱藏的錯誤會在對應的相依性圖表檔案的.suppressions 檔案中追蹤。|  
|停止隱藏選取的錯誤|以滑鼠右鍵按一下選取的隱藏的錯誤，請指向**管理驗證錯誤**，然後按一下 **停止隱藏錯誤**。<br /><br /> 選取的隱藏錯誤將會在下一次執行驗證時出現。|  
|還原所有隱藏的錯誤**錯誤清單**視窗|中的任何位置按一下滑鼠右鍵**錯誤清單**] 視窗中，指向**管理驗證錯誤**，然後按一下 [**顯示所有隱藏的錯誤**。|  
|隱藏所有隱藏的錯誤**錯誤清單**視窗|中的任何位置按一下滑鼠右鍵**錯誤清單**] 視窗中，指向**管理驗證錯誤**，然後按一下 [**隱藏所有隱藏的錯誤**。|  
  
##  <a name="ValidateAuto"></a>自動驗證程式碼  
 您可以在每次執行本機組建時執行圖層驗證。 如果您的小組使用 Team Foundation Build，可以閘道簽入來執行圖層驗證，其中您可以藉由建立自訂 MSBuild 工作來指定，以及使用組建報告收集驗證錯誤。 若要建立閘道的簽入建置，請參閱[使用閘道的簽入建置流程來驗證變更](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)。  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>在本機組建執行期間自動驗證程式碼  
  
-   使用文字編輯器來開啟模型專案 (.modelproj) 檔案，然後加入下列屬性：  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \-或-  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下模型專案包含一個或多個相依性圖表，然後按一下**屬性**。  
  
2.  在**屬性**視窗中，將模型專案**驗證架構**屬性**True**。  
  
     這會將模型專案納入驗證程序中。  
  
3.  在**方案總管 中**，按一下您想要用於驗證的相依性圖表 (.layerdiagram) 檔案。  
  
4.  在**屬性**視窗中，請確定圖表的**建置動作**屬性設定為**驗證**。  
  
     這會將相依性圖表納入驗證程序。  
  
 若要管理錯誤清單 視窗中的錯誤，請參閱[管理驗證錯誤](#ManageErrors)。  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>在 Team Foundation Build 執行期間自動驗證程式碼  
  
1.  在**Team Explorer**，按兩下組建定義，然後按**程序**。  
  
2.  在下**建置流程參數**，依序展開**編譯**，並輸入中的下列**MSBuild 引數**參數：  
  
     `/p:ValidateArchitecture=true`  
  
 如需有關驗證錯誤的詳細資訊，請參閱[了解並解決圖層驗證錯誤](#UnderstandingValidationErrors)。 如需 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 的詳細資訊，請參閱：  
  
-   [建置應用程式](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [您的建置流程中使用預設範本](http://msdn.microsoft.com/Library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [修改 UpgradeTemplate.xaml 根據舊版建置](http://msdn.microsoft.com/Library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [自訂建置流程範本](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [監視建置進度的執行](http://msdn.microsoft.com/Library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a>疑難排解圖層驗證問題  
 下列表格描述圖層驗證的問題及其解決方式。 這些問題不同於因程式碼與設計衝突而導致的錯誤。 如需有關這些錯誤的詳細資訊，請參閱[了解並解決圖層驗證錯誤](#UnderstandingValidationErrors)。  
  
|**問題**|**可能的原因**|**解決方法**|  
|---------------|------------------------|--------------------|  
|發生非預期的驗證錯誤。|驗證不適用於相依性圖表，會複製從方案總管 中的其他相依性圖表，以及屬於相同的模型專案中。 相依性圖表，如此一來會複製包含相同的參考與原始的相依性圖表。|將新的相依性圖表加入至模型專案。<br /><br /> 將來源的相依性圖表中的項目複製到新的圖表。|  
  
##  <a name="UnderstandingValidationErrors"></a>了解並解決圖層驗證錯誤  
 當您驗證相依性圖表的程式碼時，程式碼設計發生衝突時，也會發生驗證錯誤。 例如，下列條件可能造成圖層驗證發生錯誤：  
  
-   成品指派給錯誤的圖層。 在此情況下，請移動成品。  
  
-   類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。  
  
 若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 您可以透過互動方式執行這項工作。  
  
 以下章節說明用於這些錯誤的語法，解釋這些錯誤的意義，並且建議解析或管理這些錯誤的作法。  
  
|**語法**|**描述**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*是相依性圖表上的圖層相關聯的成品。<br /><br /> *ArtifactTypeN*是種*ArtifactN*，例如**類別**或**方法**，例如：<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|命名空間的名稱。|  
|*LayerNameN*|相依性圖表上的圖層名稱。|  
|*DependencyType*|相依性之間的關聯性類型*Artifact1*和*Artifact2*。 例如， *Artifact1*具有**呼叫**關聯性*Artifact2*。|  
  
|**語法錯誤**|**錯誤描述**|  
|----------------------|---------------------------|  
|DV0001:**無效的相依性**|程式碼項目 （命名空間、 類型、 成員） 對應至圖層參考程式碼項目對應到另一個圖層，但包含此圖層相依性驗證圖表中的這些圖層之間沒有任何相依性箭號時，會報告此問題。 這是相依性條件約束違規。|  
|DV1001:**無效的命名空間名稱**|此問題會回報 「 允許命名空間名稱 」 屬性不包含此程式碼項目定義所在的命名空間的圖層相關聯的程式碼項目。 這是命名的條件約束違規。 請注意，「 允許命名空間名稱 」 的語法是以分號分隔的清單中的程式碼相關聯的項目是圖層的命名空間被允許定義。|  
|DV1002: **unreferenceable 命名空間上的相依性**|此問題會回報程式碼項目與圖層相關聯，並參考另一個圖層的 「 Unreferenceable 命名空間 」 屬性中定義的命名空間中定義的程式碼項目。 這是命名的條件約束違規。 請注意，"Unreferenceable 命名空間 」 屬性定義為不應該參考與此圖層相關聯的程式碼項目中的命名空間的分號分隔清單。|  
|DV1003:**不允許命名空間名稱**|此問題會回報 「 不允許命名空間名稱 」 屬性包含此程式碼項目定義所在的命名空間的圖層相關聯的程式碼項目。 這是命名的條件約束違規。 請注意，「 不允許命名空間名稱 」 屬性定義為哪一個程式碼中與這個圖層相關聯的項目不應定義的命名空間的分號分隔清單。|  
|DV3001:**遺失的連結**|圖層 '*LayerName*'連結至'*成品*' 找不到其中。 您是否遺漏了組件參考?|*LayerName*連結至找不到的成品。 例如，類別的連結可能因為模型專案遺漏包含該類別之組件的參考而遺失。|  
|DV9001:**架構分析發現內部錯誤**|結果可能不完整。 如需詳細資訊，請參閱詳細建置事件記錄檔或輸出視窗。|如需詳細資訊，請參閱建置事件記錄檔或輸出視窗。|  

 
## <a name="see-also"></a>請參閱  
 [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)   
 [影片： 驗證您的架構相依性，即時](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
