---
title: 於部署後診斷問題 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40af4a29d35e4bd060251d0db8b6cb13dbb44caf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081004"
---
# <a name="diagnose-problems-after-deployment"></a>於部署後診斷問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要在部署後使用 IntelliTrace 診斷 ASP.NET Web App 中的問題，請包含組建資訊和版本，讓 Visual Studio 自動找出偵錯 IntelliTrace 記錄檔所需的正確原始程式檔和符號檔案。  
  
 如果使用 Microsoft Monitoring Agent 來控制 IntelliTrace，您也需要在 Web 伺服器上設定應用程式效能監視。 此功能會記錄 App 執行時的診斷事件，並將這些事件儲存至 IntelliTrace 記錄檔。 您可以接著在 Visual Studio Enterprise (但不是 Professional 或 Community 版本) 中檢視這些事件、移至發生事件的程式碼、檢視當時記錄的值，以及前後移動瀏覽執行的程式碼。 在您找到並修正問題之後，請重複建置、發行和監視發行的循環，以更早、更快解決未來可能發生的問題。  
  
 ![撰寫程式碼、建置、發行、監視、診斷、修正 ](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **您需要下列項目：**  
  
- Visual Studio 2015 或者 Team Foundation Server 2015、2013、2012 或 2010，以設定組建  
  
- Microsoft Monitoring Agent，以監視 App 及記錄診斷資料  
  
- Visual Studio Enterprise (但不是 Professional 或 Community 版本)，用以搭配 IntelliTrace 檢閱診斷資料及偵錯程式碼  
  
## <a name="SetUpBuild"></a> 步驟 1：包含在發行的組建資訊  
 設定建置流程以建立 Web 專案的建置資訊清單 (BuildInfo.config 檔案)，並在發行時包含此資訊清單。 此資訊清單包含有關專案、原始檔控制及用於建立特定組建之建置系統的資訊。 在您開啟 IntelliTrace 記錄檔之後，此資訊可協助 Visual Studio 找到相符的原始檔和符號，以檢閱記錄的事件。  
  
### <a name="AutomatedBuild"></a> 建立建置資訊清單，以使用 Team Foundation Server 進行自動化組建  
 不論使用 Team Foundation 版本控制或 Git，請遵循下列步驟。  
  
#### <a name="TFS2013"></a> Team Foundation Server 2013  
 設定組建定義，將原始檔、組建和符號的位置加入至建置資訊清單 (BuildInfo.config 檔案)。 Team Foundation Build 會自動建立此檔案並放在專案的輸出資料夾中。  
  
1. [編輯組建定義或建立新的組建定義。](http://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![檢視組建定義 TFS 2013](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. 選擇預設範本 (TfvcTemplate.12.xaml) 或您自己的自訂範本。  
  
    ![選擇建置流程範本 &#45;TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. 指定儲存符號 (PDB) 檔案的位置，以便自動編製原始檔的索引。  
  
    如果您使用自訂範本，請確定該範本含有索引來源的活動。 稍後您將加入 MSBuild 引數以指定儲存符號檔案的位置。  
  
    ![設定組建定義 TFS 2013 中的符號路徑](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    如需更多關於符號的資訊，請參閱 [發佈符號資料](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6)。  
  
4. 加入這個 MSBuild 引數可以將 TFS 和符號位置加入建置資訊清單檔案中：  
  
    **/p:IncludeServerNameInBuildInfo=True**  
  
    只要能夠存取您的 Web 伺服器，任何人都可以在建置資訊清單中看到這些位置。 確定來源伺服器是安全的。  
  
5. 如果您使用自訂範本，請加入這個 MSBuild 引數以指定儲存符號檔案的位置：  
  
    **/p:BuildSymbolStorePath=**\<符號的路徑>  
  
    ![包含組建定義 TFS 2013 中的組建伺服器資訊](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    將下列文字行加入您的 Web 專案檔 (.csproj、.vbproj)：  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. 執行新組建。  
  
   **步驟 2：**[步驟 2：發行您的應用程式](#DeployRelease)  
  
#### <a name="TFS2012_2010"></a> Team Foundation Server 2012 或 2010  
 遵循下列步驟自動建立專案的建置資訊清單 (BuildInfo.config 檔案)，並將檔案放在專案的輸出資料夾中。 此檔案在輸出資料夾中會顯示為 "*ProjectName*.BuildInfo.config"，但在發行 App 之後，部署資料夾中的相同檔案會重新命名為 "BuildInfo.config"。  
  
1. 在 Team Foundation Build Server 上安裝 Visual Studio 2013 (任一版)。  
  
2. 在您的組建定義中，指定儲存符號的位置，以便自動建立來源的索引。  
  
    如果您使用自訂範本，請確定該範本含有編製來源索引的活動。  
  
3. 將這些 MSBuild 引數加入組建定義：  
  
   - **/p:VisualStudioVersion=12.0**  
  
   - **/p:MSBuildAssemblyVersion=12.0**  
  
   - **/tv:12.0**  
  
   - **/p:IncludeServerNameInBuildInfo=True**  
  
   - **/p:BuildSymbolStorePath=**\<符號的路徑>  
  
4. 執行新組建。  
  
   **步驟 2：**[步驟 2：發行您的應用程式](#DeployRelease)  
  
### <a name="ManualBuild"></a> 建立建置資訊清單，以使用 Visual Studio 進行手動組建  
 遵循下列步驟自動建立專案的建置資訊清單 (BuildInfo.config 檔案)，並將檔案放在專案的輸出資料夾中。 此檔案在輸出資料夾中會顯示為 "*ProjectName*.BuildInfo.config"，但在發行 App 之後，部署資料夾中的相同檔案會重新命名為 "BuildInfo.config"。  
  
1. 在 [方案總管] 中上傳您的 Web 專案。  
  
2. 開啟專案檔 (.csproj、.vbproj)。 加入下列程式碼行：  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. 簽入更新的專案檔案。  
  
4. 執行新組建。  
  
   **步驟 2：**[步驟 2：發行您的應用程式](#DeployRelease)  
  
### <a name="MSBuild"></a> 建立建置資訊清單，以使用 MSBuild.exe 進行手動組建  
 當您執行組建時，會加入這些組建引數：  
  
 **/p:GenerateBuildInfoConfigFile=True**  
  
 **/p:IncludeServerNameInBuildInfo=True**  
  
 **/p:BuildSymbolStorePath=**\<符號的路徑>  
  
## <a name="DeployRelease"></a> 步驟 2：發行您的應用程式  
 如果使用在建置流程中建立的 [Web.Deploy 套件](http://msdn.microsoft.com/library/dd394698.aspx) 來部署 App，建置資訊清單的名稱會從 "*ProjectName*.BuildInfo.config" 自動重新命名為 "BuildInfo.config"，並且會放在 Web 伺服器上 App 的 Web.config 檔案所在之相同的資料夾中。  
  
 如果使用其他方法來部署 App，請確定將建置資訊清單的名稱從 "*ProjectName*.BuildInfo.config" 重新命名為 "BuildInfo.config"，並將其放在 Web 伺服器上 App 的 Web.config 檔案所在之相同的資料夾中。  
  
## <a name="step-3-monitor-your-app"></a>步驟 3：監視您的應用程式  
 在 Web 伺服器上設定應用程式效能監視功能，以便監視 App 是否發生問題、記錄診斷事件，以及將這些事件儲存至 IntelliTrace 記錄檔。 請參閱 [監視發行是否發生部署問題](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
## <a name="InvestigateEvents"></a> 步驟 4:找出問題  
 您需要在開發電腦或其他電腦上安裝 Visual Studio Enterprise，才能檢閱記錄的事件並使用 IntelliTrace 偵錯程式碼。 您也可以使用 CodeLens、偵錯工具對應和 Code Map 等工具協助診斷問題。  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>開啟 IntelliTrace 記錄檔並比對方案  
  
1. 在 Visual Studio Enterprise 2013 中開啟 IntelliTrace 記錄檔 (.iTrace 檔案)。 如果同一部電腦上也安裝了 Visual Studio Enterprise，則只需按兩下該檔案。  
  
2. 如果專案不是在方案中建置的，請選擇 [開啟方案]  ，讓 Visual Studio 自動開啟相符的方案或專案。 [問：IntelliTrace 記錄檔缺少我所部署應用程式的相關資訊。為什麼會發生這種情況？該怎麼做？](#InvalidConfigFile)  
  
     在開啟相符的方案或專案時，Visual Studio 會自動擱置所有暫止的變更。 如需關於這個擱置集的詳細資料，請查看 [輸出]  視窗或 [Team Explorer] 。  
  
     進行任何變更之前，請確認您的原始檔是否正確無誤。 如果您使用分支，您可能會在與 Visual Studio 找到相符原始檔所在的分支 (例如發行分支) 不同的分支工作。  
  
     ![從 IntelliTrace 記錄檔開啟方案](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     如果您目前有與此方案或專案對應的工作區，Visual Studio 會選取該工作區以放置找到的原始檔。  
  
     ![從原始檔控制開啟至已對應的工作區](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     否則，請選擇另一個工作區或建立新的工作區。 Visual Studio 會將整個分支對應到這個工作區。  
  
     ![從原始檔控制開啟 &#45; 建立新的工作區](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     若您要建立的工作區具有特定對應或其名稱並非您的電腦名稱，請選擇 [管理] 。  
  
     [問：Visual Studio 為何會顯示我選取的工作區不適合？](#IneligibleWorkspace)  
  
     [問：在我選擇 Team 集合或另一個集合之前，為何無法繼續執行？](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>診斷效能問題  
  
1. 在 [效能違規] 下，檢閱所記錄的效能事件、它們的總執行時間和其他事件資訊。 然後更深入發掘在特定的效能事件期間所呼叫的方法。  
  
     ![檢視效能事件詳細資料](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     您也可以直接按兩下事件。  
  
2. 在事件頁面上，檢閱這些呼叫的執行時間。 在執行樹狀結構中尋找速度緩慢的呼叫。  
  
     當您有多個呼叫 (不論是巢狀或其他形式) 時，最慢的呼叫會顯示在其專有的區段中。  
  
     展開該呼叫以檢閱在該時間點記錄的任何巢狀呼叫和值。 然後從該呼叫開始偵錯。  
  
     ![從方法呼叫開始偵錯](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     您也可以直接按兩下該呼叫。  
  
     如果該方法是位於您的應用程式程式碼中，Visual Studio 就會移至該方法。  
  
     ![從效能事件移至應用程式程式碼](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     現在您可以檢閱其他記錄值、呼叫堆疊、逐步執行程式碼，或使用 [IntelliTrace]  視窗 [在「時間」中向後或向前移動至其他方法](../debugger/intellitrace.md) (這些方法是在此效能事件期間呼叫的)。 [什麼是所有其他事件和 IntelliTrace 記錄檔中的資訊？](../debugger/using-saved-intellitrace-data.md)[我可以從這裡來做什麼？](#WhatElse)[效能事件的詳細資訊？](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  
  
### <a name="diagnose-an-exception"></a>診斷例外狀況  
  
1. 在 [例外狀況資料] 下，檢閱記錄的例外狀況事件、其類型、訊息，以及發生例外狀況的時間。 若要更深入發掘程式碼，請從例外狀況群組中最近發生的事件開始偵錯。  
  
     ![從例外狀況事件開始偵錯](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     您也可以直接按兩下事件。  
  
     如果例外狀況是發生在您的應用程式程式碼中，Visual Studio 會移至發生例外狀況的位置。  
  
     ![從例外狀況事件移至應用程式程式碼](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     現在您可以檢閱其他記錄值、呼叫堆疊，或使用 [IntelliTrace]  視窗 [在「時間」中向後或向前移動至其他記錄的事件](../debugger/intellitrace.md)、相關程式碼以及在這些時間點上記錄的值。 [IntelliTrace 記錄檔中的其他所有事件和資訊為何？](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="WhatElse"></a> 我還能如何處理？  
  
- [取得有關這個程式碼的詳細資訊](../ide/find-code-changes-and-other-history-with-codelens.md)。 尋找此程式碼的參考、其變更記錄、相關的 Bug、工作項目、程式碼檢閱或單元測試 - 只要使用編輯器中的 CodeLens 指標，就不需要離開編輯器。  
  
     ![CodeLens &#45; 檢視此程式碼的參考](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; 檢視此程式碼的變更歷程記錄](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
- [在偵錯時對應程式碼中的位置。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) 若要以視覺化方式追蹤在偵錯工作階段期間呼叫的方法，請對應呼叫堆疊。  
  
     ![偵錯期間對應呼叫堆疊](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
### <a name="FAQ"></a> 問與答  
  
#### <a name="WhyInclude"></a> 問：為什麼要在發行時包含我的專案、原始檔控制、組建和符號的相關資訊？  
 Visual Studio 使用這項資訊尋找與您嘗試偵錯之發行相符的方案和原始檔。 在您開啟 IntelliTrace 記錄檔並選取要開始偵錯的事件之後，Visual Studio 會使用符號來尋找並顯示發生事件的程式碼。 您可以接著檢視記錄的值，並前後移動瀏覽執行的程式碼。  
  
 如果使用 TFS 且此資訊不在建置資訊清單 (BuildInfo.config 檔案) 中，Visual Studio 會在您目前連接的 TFS 上尋找相符的原始檔和符號。 如果 Visual Studio 找不到正確的 TFS 或相符的原始檔，系統會提示您選擇其他 TFS。  
  
#### <a name="InvalidConfigFile"></a> 問：IntelliTrace 記錄檔缺少我所部署應用程式的相關資訊。 為什麼會發生這種情況？ 該怎麼做？  
 當您從開發電腦部署或部署期間未連接至 TFS 時，即會發生此情況。  
  
1. 移至專案的部署資料夾。  
  
2. 尋找並開啟建置資訊清單 (BuildInfo.config 檔案)。  
  
3. 確定該檔案是否包含必要資訊：  
  
- **ProjectName**  
  
   Visual Studio 中的專案名稱。 例如:   
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- 您的原始檔控制系統和下列必要屬性的相關資訊：  
  
  - **TFS**  
  
    - **ProjectCollectionUri**:您的 Team Foundation Server 和專案集合的 URI  
  
    - **ProjectItemSpec**:您的應用程式專案檔案 （.csproj 或.vbproj） 的路徑  
  
    - **ProjectVersionSpec**:您的專案版本  
  
      例如：  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Git**  
  
    - **GitSourceControl**:位置**GitSourceControl**結構描述  
  
    - **RepositoryUrl**:Team Foundation Server、 專案集合和 Git 儲存機制 URI  
  
    - **ProjectPath**:您的應用程式專案檔案 （.csproj 或.vbproj） 的路徑  
  
    - **CommitId**:您的認可識別碼  
  
      例如:   
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- **建置**  
  
   您的建置系統 ( `"TeamBuild"` 或 `"MSBuild"`) 和下列必要屬性的相關資訊：  
  
  - **BuildLabel** （適用於 TeamBuild):組建名稱和編號。 此標籤也可做為部署事件的名稱。 如需組建編號的詳細資訊，請參閱 [使用組建編號提供有意義的名稱給已完成的組建](http://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3)。  
  
  - **SymbolPath** （建議選項）：以分號分隔的符號 （PDB 檔案） 位置的 Uri 清單。 這些 URI 可以是 URL 或 UNC。 這樣可讓 Visual Studio 更容易找到相符的符號以協助您進行偵錯。  
  
  - **BuildReportUrl** （適用於 TeamBuild):在 TFS 中的組建報告位置  
  
  - **BuildId** （適用於 TeamBuild):在 TFS 中的組建詳細資料 URI。 此 URI 也可做為部署事件的 ID。 如果不是使用 TeamBuild，此 ID 必須是唯一的。  
  
  - **BuiltSolution**:Visual Studio 用於尋找及開啟相符方案之方案檔案路徑。 這是 **SolutionPath** MsBuild 屬性的內容。  
  
    例如:   
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
#### <a name="IneligibleWorkspace"></a> 問：Visual Studio 為何會顯示我選取的工作區不適合？  
 **答：** 所選取的工作區在原始檔控制資料夾和本機資料夾之間沒有任何對應。 若要建立此工作區的對應，請選擇 [管理] 。 否則，請選擇已對應的工作區或建立新的工作區。  
  
 ![在沒有已對應之工作區的情況下從原始檔控制開啟](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
#### <a name="ChooseTeamProject"></a> 問：在我選擇 Team 集合或另一個集合之前，為何無法繼續執行？  
 **答：** 下列任一原因都有可能造成此結果：  
  
- Visual Studio 未連接到 TFS。  
  
     ![從原始檔控制開啟 &#45; 未連線](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
- Visual Studio 在您目前的 Team 集合中找不到方案或專案。  
  
     當建置資訊清單檔案 (\<專案名稱>.BuildInfo.config) 未指定 Visual Studio 可以在何處找到相符的原始檔時，Visual Studio 會使用您目前連接的 TFS 尋找相符的解決方案或專案。 如果目前的 Team 集合沒有相符的來源，Visual Studio 會提示您連接至另一個 Team 集合。  
  
- Visual Studio 在建置資訊清單檔案 (\<專案名稱>.BuildInfo.config) 指定的集合中找不到解決方案或專案。  
  
     相符的來源可能已不在指定的 TFS 上，甚至可能已經不存在，原因可能是您已將該來源移轉至新的 TFS。 如果指定的 TFS 不存在，Visual Studio 可能會在約一分鐘之後逾時，然後提示您連接到另一個集合。 若要繼續，請連接至正確的 TFS 伺服器。  
  
     ![從原始檔控制開啟 &#45; 已移轉](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
#### <a name="WhatWorkspace"></a> 問：什麼是工作區？  
 **答：** 您的[工作區用於儲存來源的複本](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a)，因此您可以在簽入工作之前分別開發及測試該複本。 如果您還沒有明確對應至找到之方案或專案的工作區，則 Visual Studio 會提示您選擇可用的工作區或建立新的工作區，並以您的電腦名稱做為預設工作區名稱。  
  
#### <a name="UntrustedSymbols"></a> 問：我為什麼收到有關未受信任符號的訊息？  
 ![是否搭配未受信任的符號路徑進行偵錯？](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 **答：** 可信任的符號路徑清單中不包含建置資訊清單檔案 (\<專案名稱>.BuildInfo.config) 中的符號路徑時，就會出現此訊息。 您可以將路徑加入至偵錯工具選項中的符號路徑清單。
