---
title: 工作流程設計工具殼層功能
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4519be8ec5c5d4ba8a611df1880ae770a83cf981
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919465"
---
# <a name="workflow-designer-shell-features"></a>工作流程設計工具殼層功能

工作流程設計工具由三個主要 UI 區域所組成： 在設計工具介面、 階層連結列上方和下方的殼層。 位於畫面上方的階層連結列，會用於顯示目前根活動的祖系清單。 如需詳細資訊，請參閱[＜How to：使用階層連結巡覽](../workflow-designer/how-to-use-breadcrumb-navigation.md)。 位於畫面中央的設計介面，會用於撰寫工作流程。 位於畫面下方的殼層，會包含許多管理目前檢視的按鈕。

## <a name="shell-features"></a>殼層功能
 殼層列的右側具有按鈕，可用來縮放工作流程，將工作流程的內容調整為符合畫面的大小，以及顯示或隱藏概觀圖。 您也可使用鍵盤快速鍵 CTRL++ 和 CTRL+- 來縮放工作流程。

## <a name="overview-map"></a>概觀圖
 概觀圖會顯示在目前階層連結根目錄中整個活動的縮小版本，包含其子活動與所有展開的子活動。 檢視區是一個橘色框線的矩形，會反白顯示目前在編輯器內的活動部分。 將矩形置放於概觀圖上，即可捲動工作流程設計工具，並變更編輯器的檢視。

> [!NOTE]
> 工作流程設計工具使用者介面是虛擬化。 活動設計工具只有在需要時才會呈現。 如果從未在設計工具介面上畫出工作流程的某部分，則該部分在概觀圖上會顯示為白色。 捲動概觀圖，即可完整畫出工作流程。

## <a name="copying-or-saving-workflows-as-images"></a>將工作流程複製或儲存成影像
 工作流程能夠以點陣圖格式複製，或儲存為點陣圖或向量格式。 複製或儲存影像提供一種匯出的方式，可將目前階層連結根目錄中的整個活動檢視匯出到其他程式，包含其子活動與所有展開的子活動。

 若要複製為影像，以滑鼠右鍵按一下任何位置設計工具，然後選取**複製為影像**。 若要將儲存為映像，以滑鼠右鍵按一下任何位置設計工具，然後選取**儲存為影像**。 工作流程可儲存為 JPG、PNG、GIF 或 XPS 格式。 選取格式**另存新檔** 對話方塊中的**存檔類型：** 下拉式清單方塊，在視窗底部。

## <a name="fonts-and-colors"></a>字型和色彩

在 Visual Studio 內的工作流程設計工具中使用的字型會受到環境字型。 如果您要用於您作業系統的佈景主題中的高對比色彩配置，就會變更工作流程設計工具中顯示的色彩。 您必須重新啟動 Visual Studio 之後進行變更字型或色彩設定，才能在工作流程設計工具中所做的變更才會生效。