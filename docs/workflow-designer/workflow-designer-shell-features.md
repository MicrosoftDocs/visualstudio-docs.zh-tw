---
title: "工作流程設計工具殼層功能 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 21fa46d9d70ad69f4d3e0ccfc55f85ade331feb4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="workflow-designer-shell-features"></a>工作流程設計工具殼層功能

Windows 工作流程設計工具由三個主要 UI 區域所組成： 在設計工具介面、 階層連結列上方和下方的殼層。 位於畫面上方的階層連結列，會用於顯示目前根活動的祖系清單。 如需詳細資訊，請參閱[How to： 使用階層連結巡覽](../workflow-designer/how-to-use-breadcrumb-navigation.md)。 位於畫面中央的設計介面，會用於撰寫工作流程。 位於畫面下方的殼層，會包含許多管理目前檢視的按鈕。

## <a name="shell-features"></a>殼層功能
 殼層列的右側具有按鈕，可用來縮放工作流程，將工作流程的內容調整為符合畫面的大小，以及顯示或隱藏概觀圖。 您也可使用鍵盤快速鍵 CTRL++ 和 CTRL+- 來縮放工作流程。

## <a name="overview-map"></a>概觀圖
 概觀圖會顯示在目前階層連結根目錄中整個活動的縮小版本，包含其子活動與所有展開的子活動。 檢視區是一個橘色框線的矩形，會反白顯示目前在編輯器內的活動部分。 將矩形置放於概觀圖上，即可捲動工作流程設計工具，並變更編輯器的檢視。

> [!NOTE]
> [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 使用者介面已視覺化。 活動設計工具只有在需要時才會呈現。 如果從未在設計工具介面上畫出工作流程的某部分，則該部分在概觀圖上會顯示為白色。 捲動概觀圖，即可完整畫出工作流程。

## <a name="copying-or-saving-workflows-as-images"></a>將工作流程複製或儲存成影像
 工作流程能夠以點陣圖格式複製，或儲存為點陣圖或向量格式。 複製或儲存影像提供一種匯出的方式，可將目前階層連結根目錄中的整個活動檢視匯出到其他程式，包含其子活動與所有展開的子活動。

 若要複製為影像，以滑鼠右鍵按一下設計工具並選取**複製為影像**。 若要儲存為影像，以滑鼠右鍵按一下設計工具並選取**儲存為影像**。 工作流程可儲存為 JPG、PNG、GIF 或 XPS 格式。 選取格式**存** 對話方塊中的**存檔類型：**下拉式清單方塊，在視窗底部。

## <a name="fonts-and-colors"></a>字型和色彩

在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 內的 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]中所使用的字型會受到環境字型所控制。 如果您的作業系統主題是高對比的色彩配置，[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的顯示色彩就會變更。 變更字型或色彩設定後，必須重新啟動 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]，[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的變更才會生效。