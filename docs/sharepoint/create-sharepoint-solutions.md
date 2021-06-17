---
title: 建立 SharePoint 方案 |Microsoft Docs
description: 在 Visual Studio 中建立 SharePoint 應用程式，做為在 SharePoint Designer 中建立它們的替代方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c7a349cb79ca22869038e46d7ee27b2425119997
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113013"
---
# <a name="create-sharepoint-solutions"></a>建立 SharePoint 方案

  除了在 SharePoint Designer 中建立 SharePoint 應用程式之外，您也可以在 Visual Studio 中建立 SharePoint 應用程式。 Visual Studio 提供進階偵錯工具、IntelliSense、陳述式完成和專案範本等功能，可加速開發 SharePoint。 Visual Studio 也利用進階 .NET Framework 工具和語言。 您可以使用 Visual Basic 或 Visual C# 開發 SharePoint 專案，並且可以使用 JavaScript 開發 SharePoint 專案的應用程式。

> [!NOTE]
> 了解如何使用新的 [SharePoint 增益集模型](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) ，以擴充使用者的 SharePoint 體驗。 相較於 SharePoint 解決方案，這些增益集的使用量非常小，而且幾乎可以使用 HTML5、JavaScript、CSS3 和 XML 等任何 Web 程式設計技術來建置。

|內容區域|文章|
|-|-|
|![文件集](../sharepoint/media/vs-icon-documentation.gif "文件")|**文件集**<br /><br /> -   [在 Visual Studio&#41;中開始 &#40;SharePoint 開發 ](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)<br />-   [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [建立和調試 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|
|![文件集](../sharepoint/media/vs-icon-documentation.gif "文件")|**精選工作**<br /><br /> -   [逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [如何：建立 SharePoint Web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [如何：為 SharePoint 應用程式頁面或 web 元件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![逐步解說](../sharepoint/media/vs-icon-walkthroughs.gif "逐步解說")|**逐步解說**<br /><br /> -   [SharePoint 開發逐步解說](../sharepoint/sharepoint-development-walkthroughs.md)|
|![程式碼範例](../sharepoint/media/vs-icon-codesamples.gif "程式碼範例")|**程式碼範例**<br /><br /> -   [SharePoint 開發範例](../sharepoint/sharepoint-development-samples.md)<br />-   [SharePoint 開發人員下載](/sharepoint/dev/)|
|![訓練](../sharepoint/media/vs-icon-training.gif "訓練")|**訓練**<br /><br /> -   [學習 SharePoint 開發](/sharepoint/dev/)|
|![論壇](../sharepoint/media/vs-icon-forums.gif "論壇")|**論壇**<br /><br /> -   [使用 Visual Studio 的 SharePoint 開發](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment)<br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![訓練](../sharepoint/media/vs-icon-training.gif "訓練")|**部落格**<br /><br /> -   [Visual Studio SharePoint 開發 Blog](/archive/blogs/vssharepointtoolsblog/)|
|![如何？視頻](../sharepoint/media/vs-icon-howdoivideos.gif "如何？視頻")|**如何？視頻**<br /><br /> -   [如何：在 Visual Studio 2010 中建立適用于 SharePoint 2010 的 Visual Web 組件？](https://visualstudio.microsoft.com/)<br />-   [如何：在 Visual Studio 2010 中建立 SharePoint 2010 的內容類型？](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [如何：在 Visual Studio 2010 中建立 SharePoint 2010 的網站定義？](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [如何：使用 Visual Studio 2010 建立適用于 SharePoint 2010 的商務資料連線模型？](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Channel 9 影片](../sharepoint/media/vs-icon-channel9videos.gif "Channel 9 的影片")|**Channel 9 影片**<br /><br /> -   [Visual Studio 2010 中的 SharePoint 開發總覽](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010)<br />-   [使用 Visual Studio 2010 建立 SharePoint 2010 Web 組件的最佳作法](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010)<br />-   [Visual Studio 2010 中的 SharePoint 功能與封裝設計工具](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010)|
|![開發人員中心](../sharepoint/media/vs-icon-msdndevcenter.gif "開發人員中心")|**開發人員中心**<br /><br /> -   [Visual Studio 開發中心](https://visualstudio.microsoft.com/)<br />-   [SharePoint 開發人員中心](/sharepoint/dev/)<br />-   [SharePoint Server 開發人員中心](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [SharePoint Designer 開發人員中心](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [ASP.NET 開發人員中心](/previous-versions/msdn10/aa336522(v=msdn.10))|
|![提供意見反應](../sharepoint/media/vs-icon-feedback.gif "提供意見反應")|**提供意見反應**<br /><br /> 提供有關 Visual Studio 的意見反應：<br /><br /> -   [Microsoft Connect](/collaborate/connect-redirect)<br /><br /> 提供有關 Visual Studio 文件的意見反應：<br /><br /> -   **輕量視圖。** 如果您在任何主題的頂端，您可以選擇 [為這個主題評分]  連結跳至該主題的底部，然後指定 [是]  或 [否]  以回應 [本文對您有任何幫助嗎？]  。如果選擇 [否] ，可接著選取一或多個出現的核取方塊，及 (或) 在文字方塊中提供更多資訊。 完成後，請選擇 [提交]  按鈕。<br />-   **Scriptfree View。** 在主題頂端，選擇 [ **意見** 反應] 連結，在 TechNet 和 Expression Library 意見反應論壇中提供意見反應。<br />-   **傳統視圖。** 在主題頂端，選擇 [意見反應]  圖示，將有關該主題的意見反應提供給文件小組。|
