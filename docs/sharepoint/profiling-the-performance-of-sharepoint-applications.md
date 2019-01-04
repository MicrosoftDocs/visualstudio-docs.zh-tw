---
title: 剖析 SharePoint 應用程式的效能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8578a27dc6daceda25667142a3cdccae50a42552
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905685"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>分析 SharePoint 應用程式的效能

如果您的 SharePoint 應用程式執行緩慢或無效率，您可以使用 Visual Studio 中的程式碼剖析功能識別有問題的程式碼和其他項目。 藉由使用 負載測試功能，您可以決定 SharePoint 應用程式承受壓力，例如當許多使用者存取應用程式同時執行的方式。 藉由執行 web 效能測試，您可以測量應用程式在網站上的執行方式。 藉由使用自動程式化的 UI 測試，您可以確認整個 SharePoint 應用程式，包括其使用者介面中，是否正確運作。 當您一起使用這些測試時，它們可以協助您部署應用程式之前，請找出效能問題。

## <a name="profile-tools-overview"></a>設定檔工具概觀

程式碼剖析指的是觀察和記錄您的應用程式的效能行為，因為它會執行的程序。 透過分析您的應用程式，您可以發現問題，例如瓶頸、 沒有效率的程式碼和記憶體配置問題，導致應用程式執行速度變慢，或使用太多記憶體。 比方說，您可以使用程式碼剖析識別程式碼，也就是常被稱為和您的應用程式的整體效能變慢的程式碼區段作用點。 您識別作用區之後，通常可以最佳化，或排除它們。

您可以使用整合式的開發環境 (IDE) 中的數個程式碼剖析工具，識別並找出這類效能問題。 這些工具運作 SharePoint 專案相同的方式，針對其他種類的 Visual Studio 專案所顯示的一樣。 程式碼剖析工具效能精靈會引導您完成建立效能工作階段，會使用您指定的測試。 效能工作階段是一組用於收集效能資訊從應用程式，以及一或多個程式碼剖析執行結果的組態資料。 效能工作階段會儲存在專案資料夾中，而且您可以檢視在**效能總管**。 如需詳細資訊，請參閱[了解效能收集方法](../profiling/understanding-performance-collection-methods.md)。

建立後，當您在您的應用程式上執行設定檔分析時，報表會提供關於其效能的詳細資料。 此報表可能包含不同時間、 階層式的函式呼叫堆疊或呼叫樹狀結構的圖形等的 CPU 使用量的項目。 報表的確切內容有所不同，您執行，例如取樣或檢測的測試類型。 如需詳細資訊，請參閱 <<c0> [ 程式碼剖析工具報告概觀](http://go.microsoft.com/fwlink/?LinkId=224689)。

## <a name="performance-session-process"></a>效能工作階段的程序

若要分析應用程式，您開始使用程式碼剖析工具效能精靈建立效能工作階段。 在功能表列上選擇 **分析**，**啟動效能精靈**。 當您完成精靈時，您會輸入效能工作階段，例如您想要的剖析方法以及您想要剖析的應用程式所需的資訊。 如需詳細資訊，請參閱[＜How to：網站或使用 [效能精靈] 的 Web 應用程式程式碼剖析](http://go.microsoft.com/fwlink/?LinkId=224692)。 或者，您可以使用命令列選項來設定和執行效能工作階段。 如需詳細資訊，請參閱 <<c0> [ 程式碼剖析工具從命令列使用](http://go.microsoft.com/fwlink/?LinkId=224703)。 如果您想要手動設定效能工作階段的各個層面，請參閱[How to:使用 程式碼剖析工具，手動建立效能工作階段](http://go.microsoft.com/fwlink/?LinkId=224691)。 您也可以建立效能工作階段從單元測試，在**測試結果**視窗中，開啟單元測試的捷徑功能表，然後選擇**建立效能工作階段**。

設定效能工作階段之後，儲存工作階段組態、 伺服器設定為提供程式碼剖析資料，和執行應用程式。 當您使用應用程式時，效能資料會寫入至記錄檔。 效能工作階段都會列入**效能總管**下方**目標**資料夾。 在效能工作階段完成之後，它的報表會出現在**報表**中的資料夾**效能總管**。 若要顯示報表，請開啟它**效能總管**。 若要檢視或設定效能工作階段的屬性，開啟其捷徑功能表中的**效能總管**，然後選擇**屬性**。 如需效能工作階段的特定屬性的詳細資訊，請參閱[設定程式碼剖析工具效能工作階段](http://go.microsoft.com/fwlink/?LinkId=224694)。 如需如何解譯結果的效能工作階段資訊，請參閱[分析程式碼剖析工具資料](http://go.microsoft.com/fwlink/?LinkId=224704)。

## <a name="stress-test"></a>壓力測試

您可以在 Visual Studio 中建立負載測試和 web 效能測試，以分析您的應用程式的壓力效能。 當您在 Visual Studio 中建立負載測試時，您會指定因數，稱為案例中，若要測試您的應用程式的組合。 這些因素包含負載模式、 測試混合模型、 測試混合、 網路混合和 web 瀏覽器混合。 負載測試情節可以包含單元測試和 web 效能測試。

圖 1：負載測試結果範例

![執行負載測試圖形檢視](../sharepoint/media/load-webgraphs.png "執行負載測試圖形檢視")

Web 效能測試會模擬使用者可能會如何互動的 SharePoint 應用程式。 在瀏覽器工作階段中錄製 HTTP 要求，或使用，您可以建立 web 效能測試**Web 效能測試錄製器**。 Web 要求會出現在**Web 效能測試編輯器**瀏覽器工作階段完成之後。 您可以再偵錯中的結果**Web 效能測試結果檢視器**。 您可以使用，以手動建置 web 效能測試**Web 效能測試編輯器**。

## <a name="test-user-interfaces"></a>測試使用者介面

自動程式化的 UI 測試自動驅動您的 SharePoint 應用程式，透過其使用者介面 (UI)。 這些測試涵蓋 UI 控制項，例如按鈕和功能表，以確認它們正常運作。 這種測試是執行驗證或其他邏輯是在 UI 中，例如在網頁上的情況特別有用。 您也可以使用自動程式化的 UI 測試來自動化手動測試。 您建立自動程式化 UI 測試 SharePoint 應用程式相同的方式隨著您建立其他類型的應用程式的測試。 如需詳細資訊，請參閱 <<c0> [ 測試 SharePoint 2010 應用程式使用自動程式化 UI 測試](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：分析 SharePoint 應用程式](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|示範如何在 SharePoint 應用程式上執行取樣分析。|
|[在發行前對您的應用程式執行效能測試](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|描述如何建立負載測試，可協助您進行壓力測試 SharePoint 應用程式。|
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|描述如何使用單元測試程式碼中找出邏輯錯誤。|
|[使用自動程式化 UI 測試來測試 SharePoint 2010 應用程式](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|說明如何測試 SharePoint 應用程式的使用者介面。|

## <a name="see-also"></a>另請參閱

- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [改善程式碼品質](../test/improve-code-quality.md)