---
title: 使用舊版工作流程設計工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794b52c918eb727fe67d24af209d21403da18475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975464"
---
# <a name="using-the-legacy-workflow-designer"></a>使用舊版工作流程設計工具

由 Visual Studio 2010 工作流程設計工具提供的舊版可以用於以.NET Framework 3.5 版或 WinFX 目標。

存取選取 **.NET Framework 3.0**選項或 **.NET Framework 3.5**在清單頂端的下拉式選項**新專案**視窗。 Visual Studio 2010 中的預設選項是 **.NET Framework 4**用來建立目標為.NET Framework 4 的 Windows Workflow Foundation (WF) 應用程式。

工作流程設計工具可用來以圖形方式建立使用熟悉的 Visual Studio 使用者介面的 Windows Workflow Foundation (WF) 應用程式。 Windows Workflow Foundation (WF) 應用程式是由稱做活動的工作流程處理程序步驟所組成。 若要建立工作流程，撰寫活動在設計介面上的拖曳其各自的活動設計工具從**工具箱**拖曳至設計介面。

下表列出 Visual Studio for Windows Workflow Foundation 的主要功能。

|功能|描述|
|-------------|-----------------|
|活動拖放|將活動從**工具箱**拖曳至設計介面，來建立工作流程。|
|屬性瀏覽器|標準**屬性**Visual Studio 中的視窗用來設定活動內容。|
|縮放|雙筒望遠鏡**縮放層級**圖示位於設計介面右側的垂直捲軸列下方。 按一下雙筒望遠鏡並選取縮放百分比，可讓工作流程圖放大或縮小。您也可以使用**取景位置調整**圖示的放大鏡游標選項來放大和縮小。|
|移動瀏覽|**取景位置調整**圖示，含有四個交叉的箭頭指向 4 個方向，位於右邊的雙筒望遠鏡縮放圖示的正下方的設計介面上的垂直捲軸列下方。 如果您按一下平移圖示，會顯示快顯功能表來提供以下的游標選項：<br /><br /> -**放大**放大鏡游標讓您放大按一下設計介面。<br />-**縮小**放大鏡游標讓您按一下設計介面，即可縮小。<br />-**巡覽工具**手狀游標可讓您 「 抓住 」 然後平移工作流程設計介面中的檢視。<br />-**預設**箭頭游標可讓您從其他資料指標切換回預設的箭頭游標。|
|自動捲動|如果您的工作流程很大，有時可能需要在設計介面區域的可視範圍外放置活動。 Visual Studio 可讓您拖曳邊緣，最接近您要放置活動的設計介面的活動。 設計介面檢視會自動往該方向捲動。|
|智慧標籤|設定不完整或是設定無效的活動會以驚嘆號圖示標記。 您可以按一下圖示，便會看到一個下拉式清單，其中列出活動中的組態需求。 然後您可以使用**屬性**適當地設定活動的視窗。 當活動的所有屬性都有效時，驚嘆號圖示便會消失。|

## <a name="see-also"></a>另請參閱

- [開發工作流程](http://go.microsoft.com/fwlink?LinkID=65010)