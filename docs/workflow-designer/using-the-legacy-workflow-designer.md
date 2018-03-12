---
title: "使用舊版工作流程設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a042d98019b7f618792f7a9104d262362a4e6e3d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="using-the-legacy-workflow-designer"></a>使用舊版工作流程設計工具
[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 提供的舊版 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 可用來以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標。

 存取選取**.NET Framework 3.0**選項或**.NET Framework 3.5**在清單頂端的下拉式選項**新專案**視窗。 中的預設選項[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**用來建立[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]目標的應用程式[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]。

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 提供了一種以圖形方式使用熟悉的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 使用者介面建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 應用程式。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式是由稱做活動的工作流程程序步驟所組成。 若要建立工作流程，撰寫活動在設計介面上的拖曳其各自的活動設計工具從**工具箱**拖曳至設計介面。

 下表列出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] for Windows Workflow Foundation 的主要功能。

|功能|描述|
|-------------|-----------------|
|活動拖放|將活動從**工具箱**拖曳至設計介面，來建立工作流程。|
|屬性瀏覽器|標準**屬性**視窗[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用來設定活動內容。|
|縮放|雙筒望遠鏡**縮放層級**圖示位於設計介面右側的垂直捲軸列下方。 按一下雙筒望遠鏡並選取縮放百分比，可讓工作流程圖放大或縮小。您也可以使用**取景位置調整**圖示的放大鏡游標選項來放大和縮小。|
|移動瀏覽|**取景位置調整**圖示，含有四個交叉的箭頭指向 4 個方向，位於右邊的雙筒望遠鏡縮放圖示的正下方的設計介面上的垂直捲軸列下方。 如果您按一下平移圖示，會顯示快顯功能表來提供以下的游標選項：<br /><br /> -**放大**放大鏡游標讓您放大按一下設計介面。<br />-**縮小**放大鏡游標讓您按一下設計介面，即可縮小。<br />-**巡覽工具**手狀游標可讓您 「 抓住 」 然後平移工作流程設計介面中的檢視。<br />-**預設**箭頭游標可讓您從其他資料指標切換回預設的箭頭游標。|
|自動捲動|如果您的工作流程很大，有時可能需要在設計介面區域的可視範圍外放置活動。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可讓您將活動拖曳到設計介面的邊緣，靠近您要放置活動的地方。 設計介面檢視會自動往該方向捲動。|
|智慧標籤|設定不完整或是設定無效的活動會以驚嘆號圖示標記。 您可以按一下圖示，便會看到一個下拉式清單，其中列出活動中的組態需求。 然後您可以使用**屬性**適當地設定活動的視窗。 當活動的所有屬性都有效時，驚嘆號圖示便會消失。|

## <a name="see-also"></a>另請參閱

- [開發工作流程](http://go.microsoft.com/fwlink?LinkID=65010)