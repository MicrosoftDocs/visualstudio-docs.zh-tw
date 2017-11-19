---
title: "程式碼剖析 SharePoint 應用程式的效能 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0effe0190d54d05d706127a8e5fada66af1c7ab6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>剖析 SharePoint 應用程式的效能
  如果您的 SharePoint 應用程式正在執行速度很慢或沒有效率，您可以使用 Visual Studio 中的程式碼剖析功能來識別問題的程式碼和其他項目。 藉由使用負載測試功能，您可以判斷在資源不足時，例如當許多使用者存取應用程式同時執行 SharePoint 應用程式的方式。 藉由執行 web 效能測試，您可以測量應用程式從網站上的執行方式。 您可以藉由使用自動程式化的 UI 測試，確認整個 SharePoint 應用程式，包括其使用者介面，是否能正常運作。 當您一起使用這些測試時，它們可以協助您識別效能問題，然後再部署應用程式。  
  
## <a name="profiling-tools-overview"></a>程式碼剖析工具概觀  
 程式碼剖析是指的觀察和錄製您的應用程式的效能行為，在執行程序。 程式碼剖析應用程式，您能夠發現問題，例如瓶頸、 沒有效率的程式碼，以及記憶體配置問題，導致應用程式執行速度變慢，或使用太多記憶體。 例如，您可以使用程式碼剖析來識別您的程式碼，也就是，經常呼叫和您的應用程式的整體效能變慢的程式碼區段的作用。 識別作用點之後，您經常可以最佳化，或將它們移除。  
  
 您可以使用整合式的開發環境 (IDE) 中的數個程式碼剖析工具，找出並找出這類效能問題。 這些工具的運作方式相同 SharePoint 專案與對於其他類型的 Visual Studio 專案。 程式碼剖析工具效能精靈將引導您完成建立效能工作階段，會使用您指定的測試。 效能工作階段是一組用於收集應用程式，以及一或多個分析回合的結果中的效能資訊的組態資料。 效能工作階段會儲存在專案資料夾，而且您可以檢視在**效能總管**。 如需詳細資訊，請參閱[了解效能收集方法](/visualstudio/profiling/understanding-performance-collection-methods)。  
  
 建立和執行設定檔分析應用程式之後，報表會提供有關其效能詳細資料。 這份報表可以包含項目，例如圖表的 CPU 使用率時間、 階層式的函式呼叫堆疊，或呼叫樹狀結構。 依據執行，例如取樣或檢測測試類型，可能會報告的確切內容。 如需詳細資訊，請參閱[程式碼剖析工具報告概觀](http://go.microsoft.com/fwlink/?LinkId=224689)。  
  
## <a name="performance-session-process"></a>效能工作階段流程  
 若要分析應用程式，您開始使用程式碼剖析工具效能精靈來建立效能工作階段。 在功能表列上選擇 **分析**，**啟動效能精靈**。 當您完成精靈時，您會輸入效能工作階段，例如您想要的設定檔方法，以及您要分析的應用程式所需的資訊。 如需詳細資訊，請參閱[How to： 設定檔的網站或 Web 應用程式使用效能精靈](http://go.microsoft.com/fwlink/?LinkId=224692)。 或者，您可以使用命令列選項來設定及執行效能工作階段。 如需詳細資訊，請參閱[使用程式碼剖析工具從命令列](http://go.microsoft.com/fwlink/?LinkId=224703)。 如果您想要手動設定每個層面的效能工作階段，請參閱[How to： 手動建立效能工作階段的程式碼剖析工具](http://go.microsoft.com/fwlink/?LinkId=224691)。 您也可以建立效能工作階段從單元測試的方法是，在**測試結果**視窗中，開啟單元測試的捷徑功能表，然後選擇**建立效能工作階段**。  
  
 設定效能工作階段之後，工作階段設定會儲存、 伺服器設定為提供程式碼剖析資料，並執行應用程式。 當您使用應用程式時，效能資料會寫入至記錄檔。 效能工作階段中所列**效能總管**下**目標**資料夾。 效能工作階段完成之後，它的報表會出現在**報表**資料夾中的**效能總管**。 若要顯示報表，請開啟在**效能總管**。 若要檢視或設定效能工作階段的屬性，開啟其捷徑功能表中的**效能總管**，然後選擇 **屬性**。 如需效能工作階段的特定屬性的詳細資訊，請參閱[設定程式碼剖析工具效能工作階段](http://go.microsoft.com/fwlink/?LinkId=224694)。 如需如何解譯效能工作階段的結果資訊，請參閱[分析程式碼剖析工具資料](http://go.microsoft.com/fwlink/?LinkId=224704)。  
  
## <a name="stress-testing"></a>壓力測試  
 藉由建立負載測試和 web 效能測試，在 Visual Studio Ultimate 中，您可以分析您的應用程式的壓力效能。 當您在 Visual Studio 中建立負載測試時，您可以指定多種因素而定，呼叫案例中，若要對測試應用程式。 這些因素包括負載模式、 測試混合模型、 測試混合、 網路混合和 web 瀏覽器混合。 負載測試情節可以包含單元測試和 web 效能測試。  
  
 圖 1： 負載測試結果範例  
  
 ![執行中負載測試圖形檢視](../sharepoint/media/load-webgraphs.png "執行負載測試圖形檢視")  
  
 Web 效能測試會模擬使用者可能會與 SharePoint 應用程式互動的方式。 您可以建立 web 效能測試，在瀏覽器工作階段中錄製 HTTP 要求，或使用**Web 效能測試錄製器**。 Web 要求出現在**Web 效能測試編輯器**瀏覽器工作階段完成之後。 您可以再偵錯中的結果**Web 效能測試結果檢視器**。 您可以使用，以手動建立 web 效能測試**Web 效能測試編輯器**。  
  
## <a name="testing-user-interfaces"></a>測試使用者介面  
 自動程式化的 UI 測試會透過其使用者介面 (UI)，自動驅動 SharePoint 應用程式。 這些測試涵蓋的 UI 控制項，例如按鈕和功能表，以確認它們正確運作。 這種測試是驗證或其他邏輯執行在 UI 中，例如在網頁中特別有用。 您也可以使用自動程式化的 UI 測試來自動化手動測試。 您建立的自動程式化 UI 測試 SharePoint 應用程式相同的方式就像建立其他類型應用程式的測試。 如需詳細資訊，請參閱[測試 SharePoint 2010 應用程式使用自動程式化 UI 測試](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[逐步解說：剖析 SharePoint 應用程式](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|示範如何在 SharePoint 應用程式上執行取樣基本資料分析。|  
|[在發行前對您的應用程式執行效能測試](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|描述如何建立負載測試，協助您進行壓力測試 SharePoint 應用程式。|  
|[對程式碼進行單元測試](/visualstudio/test/unit-test-your-code)|描述如何使用單元測試程式碼中找出邏輯錯誤。|  
|[使用自動程式化 UI 測試來測試 SharePoint 2010 應用程式](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|說明如何測試 SharePoint 應用程式的使用者介面。|  
  
## <a name="see-also"></a>另請參閱  
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [測試應用程式](/devops-test-docs/test/test-apps-early-and-often)   
 [改善程式碼品質](/visualstudio/test/improve-code-quality)  
  
  