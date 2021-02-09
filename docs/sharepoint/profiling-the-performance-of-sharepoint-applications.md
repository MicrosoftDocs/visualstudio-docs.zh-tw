---
title: 分析 SharePoint 應用程式的效能 |Microsoft Docs
description: 如果 SharePoint 應用程式的執行速度變慢或效率不高，請分析這些應用程式的效能。 使用 Visual Studio 分析功能來尋找有問題的程式碼。
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d59f5b472f791f9774515cdb3e92cc4cf7f9f55b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860733"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>分析 SharePoint 應用程式的效能

如果您的 SharePoint 應用程式執行緩慢或效率不佳，您可以使用 Visual Studio 中的程式碼剖析功能來識別有問題的程式碼和其他元素。 藉由使用負載測試功能，您可以決定 SharePoint 應用程式在壓力下執行的方式，例如，當許多使用者同時存取應用程式時。 藉由執行 web 效能測試，您可以測量應用程式在 web 上的執行方式。 藉由使用自動程式碼 UI 測試，您可以確認整個 SharePoint 應用程式（包括其使用者介面）是否正常運作。 當您一起使用這些測試時，它們可以在部署應用程式之前協助您找出效能問題。

## <a name="profile-tools-overview"></a>設定檔工具總覽

分析指的是在應用程式執行時觀察並記錄其效能行為的程式。 藉由分析您的應用程式，您可以發現瓶頸、無效率的程式碼和記憶體配置問題等問題，這會導致應用程式執行速度變慢或使用過多的記憶體。 例如，您可以流量分析來識別程式碼中的作用區，這是經常呼叫的程式碼區段，而且可能會降低應用程式的整體效能。 在您找出熱點之後，通常可以將它們優化或消除。

您可以在整合式開發環境中使用數種程式碼剖析工具 (IDE) 找出並找出這些類型的效能問題。 這些工具對 SharePoint 專案的運作方式與其他種類的 Visual Studio 專案相同。 分析工具 Performance Wizard 會引導您建立使用您指定之測試的效能會話。 效能會話是一組設定資料，可用來從應用程式收集效能資訊，以及一或多個程式碼剖析執行的結果。 效能會話會儲存在您的專案資料夾中，您可以在 **效能總管** 中加以查看。 如需詳細資訊，請參閱[了解效能收集方法](../profiling/understanding-performance-collection-methods.md)。

在您于應用程式上建立並執行設定檔分析之後，報表會提供其效能的詳細資料。 這份報表可包含一段時間的 CPU 使用量圖表、階層式函式呼叫堆疊或呼叫樹狀結構等專案。 根據您所執行的測試類型（例如取樣或檢測），報表的確切內容可能會有所不同。 如需詳細資訊，請參閱 [分析工具報表總覽](../profiling/performance-report-overview.md)。

## <a name="performance-session-process"></a>效能會話進程

若要分析應用程式，請先流量分析工具 Performance Wizard 建立效能會話。 在功能表列上，選擇 [ **分析**]、[ **啟動效能分析]**。 當您完成嚮導時，請輸入您的效能會話所需的資訊，例如您想要的設定檔方法，以及您想要分析的應用程式。 如需詳細資訊，請參閱 [如何：使用效能 Wizard 分析網站或 Web 應用程式](../profiling/how-to-collect-performance-data-for-a-web-site.md)。 或者，您可以使用命令列選項來設定和執行效能會話。 如需詳細資訊，請參閱 [從命令列流量分析工具](../profiling/using-the-profiling-tools-from-the-command-line.md)。 如果您想要手動設定效能會話的每個層面，請參閱 [如何：流量分析工具手動建立效能會話](../profiling/how-to-manually-create-performance-sessions.md)。 您也可以在 [ **測試結果** ] 視窗中，開啟單元測試的快捷方式功能表，然後選擇 [ **建立效能會話**]，在單元測試中建立效能會話。

設定效能會話之後，會儲存會話設定、設定伺服器以提供程式碼剖析資料，以及執行應用程式。 當您使用應用程式時，會將效能資料寫入至記錄檔。 效能會話會列在 **效能總管** 的 [ **目標** ] 資料夾底下。 在效能會話完成後，它的報表就會出現在 **效能總管** 的 [**報表**] 資料夾中。 若要顯示報表，請在 **效能總管** 中開啟報表。 若要查看或設定效能會話的屬性，請在 **效能總管** 中開啟其快捷方式功能表，然後選擇 [ **屬性**]。 如需有關效能會話特定屬性的詳細資訊，請參閱設定 [分析工具的效能會話](../profiling/configuring-performance-sessions.md)。 如需有關如何解讀效能會話結果的詳細資訊，請參閱 [分析分析工具資料](../profiling/analyzing-performance-tools-data.md)。

## <a name="stress-test"></a>壓力測試

您可以藉由在 Visual Studio 中建立負載測試和 web 效能測試，來分析應用程式的壓力效能。 當您在 Visual Studio 中建立負載測試時，您會指定用來測試應用程式的因素（稱為案例）的組合。 這些因素包括負載模式、測試混合模型、測試混合、網路混合和網頁瀏覽器混合。 負載測試情節可以包含單元測試和 web 效能測試。

圖1：負載測試結果範例

![執行負載測試圖形檢視](../sharepoint/media/load-webgraphs.png "執行負載測試圖形檢視")

Web 效能測試會模擬終端使用者如何與 SharePoint 應用程式互動。 您可以藉由在瀏覽器會話中記錄 HTTP 要求，或使用 **Web 效能測試錄製** 器來建立 web 效能測試。 當瀏覽器會話完成之後，web 要求會出現在 **Web 效能測試編輯器** 中。 然後，您可以在 **Web 效能測試結果檢視器** 中，對結果進行 debug 錯。 您也可以使用 **Web 效能測試編輯器** 手動建立 web 效能測試。

## <a name="test-user-interfaces"></a>測試使用者介面

自動程式碼 UI 測試會透過使用者介面 (UI) ，自動驅動您的 SharePoint 應用程式。 這些測試涵蓋 UI 控制項（例如按鈕和功能表），以確認它們是否正確運作。 如果在 UI 中執行驗證或其他邏輯（例如在網頁中），這種測試就特別有用。 您也可以使用自動程式碼 UI 測試來自動化手動測試。 建立 SharePoint 應用程式的自動程式碼 UI 測試的方式，與為其他類型應用程式建立測試的方式相同。 如需詳細資訊，請參閱使用自動程式 [代碼 UI 測試來測試 SharePoint 2010 應用程式](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：分析 SharePoint 應用程式](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|示範如何在 SharePoint 應用程式上執行取樣設定檔分析。|
|[在發行前對您的應用程式執行效能測試](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|描述如何建立負載測試，以協助您對 SharePoint 應用程式進行壓力測試。|
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|描述如何使用單元測試找出程式碼中的邏輯錯誤。|
|[使用自動程式碼 UI 測試來測試 SharePoint 2010 應用程式](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|說明如何測試 SharePoint 應用程式的使用者介面。|

## <a name="see-also"></a>另請參閱

- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [改善程式碼品質](../test/improve-code-quality.md)