---
title: 使用舊版工作流程設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302788"
---
# <a name="using-the-legacy-workflow-designer"></a>使用舊版工作流程設計工具
[!INCLUDE[wfd2](../includes/wfd2-md.md)] 提供的舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 可用來以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 為目標。

 您可以在 [**新增專案**] 視窗頂端的下拉式清單中，選取 [ **.NET Framework 3.0** ] 選項或 [ **.NET Framework 3.5** ] 選項來存取它。 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中的預設選項為 **.NET Framework 4** ，用來建立以 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]為目標的 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式。

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 提供了一種以圖形方式使用熟悉的 [!INCLUDE[wf](../includes/wf-md.md)] 使用者介面建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式。 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式是由稱做活動的工作流程程序步驟所組成。 若要建立工作流程，請在設計介面上撰寫活動，方法是將其各自的活動設計工具從 [**工具箱**] 拖曳至設計介面上。

 下表列出 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] for Windows Workflow Foundation 的主要功能。

|功能|描述|
|-------------|-----------------|
|活動拖放|將活動從 [**工具箱**] 拖曳至設計介面，以建立工作流程。|
|屬性瀏覽器|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的標準 [**屬性**] 視窗會用來設定活動的屬性。|
|縮放|雙筒**縮放層級**圖示位於設計介面右側的垂直捲動條底下。 按一下 [望遠鏡] 並選取 [縮放百分比]，讓工作流程圖形放大或縮小。您也可以使用 [**平移**] 圖示放大鏡游標選項來放大和縮小。|
|取景位置調整|[**平移**] 圖示是一個包含四個交叉箭號的圓形，指向四個方向，位於設計介面右側的垂直捲動條下方，就在雙望遠鏡縮放圖示的正下方。 如果您按一下平移圖示，會顯示快顯功能表來提供以下的游標選項：<br /><br /> -**放大**放大鏡游標可讓您按一下設計介面來放大。<br />-[**縮小**] 放大鏡游標可讓您按一下設計介面來縮小。<br />-**導覽工具**手形游標可讓您「抓取」，並在設計介面中切換工作流程的視圖。<br />-**預設**箭號游標可讓您將其他游標切換回預設箭號游標。|
|自動捲動|如果您的工作流程很大，有時可能需要在設計介面區域的可視範圍外放置活動。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可讓您將活動拖曳到設計介面的邊緣，靠近您要放置活動的地方。 設計介面檢視會自動往該方向捲動。|
|智慧標籤|設定不完整或是設定無效的活動會以驚嘆號圖示標記。 您可以按一下圖示，便會看到一個下拉式清單，其中列出活動中的組態需求。 接著，您可以使用 [**屬性**] 視窗來適當地設定活動。 當活動的所有屬性都有效時，驚嘆號圖示便會消失。|

## <a name="in-this-section"></a>本節內容
 [Visual Studio 工作流程視窗 (舊版)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)

 [循序工作流程檢視 (舊版)](../workflow-designer/sequential-workflow-views-legacy.md)

 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)

 [在工作流程中使用佈景主題 (舊版)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [使用舊版狀態機器工作流程設計工具](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)

 [舊版 Windows Workflow Foundation UI 設計工具的說明](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>另請參閱
 [開發工作流程](https://go.microsoft.com/fwlink?LinkID=65010)