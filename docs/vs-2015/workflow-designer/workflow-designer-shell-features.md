---
title: 工作流程設計工具 Shell 功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606592"
---
# <a name="workflow-designer-shell-features"></a>工作流程設計工具殼層功能
[!INCLUDE[wfd1](../includes/wfd1-md.md)] 是由三個主要 UI 區域構成：設計工具介面、上方的階層連結列和下方的殼層。 位於畫面上方的階層連結列，會用於顯示目前根活動的祖系清單。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][如何：使用](../workflow-designer/how-to-use-breadcrumb-navigation.md)階層連結導覽。 位於畫面中央的設計介面，會用於撰寫工作流程。 位於畫面下方的殼層，會包含許多管理目前檢視的按鈕。

## <a name="shell-features"></a>殼層功能
 殼層列的右側具有按鈕，可用來縮放工作流程，將工作流程的內容調整為符合畫面的大小，以及顯示或隱藏概觀圖。 您也可使用鍵盤快速鍵 CTRL++ 和 CTRL+- 來縮放工作流程。

## <a name="overview-map"></a>概觀圖
 概觀圖會顯示在目前階層連結根目錄中整個活動的縮小版本，包含其子活動與所有展開的子活動。 檢視區是一個橘色框線的矩形，會反白顯示目前在編輯器內的活動部分。 將矩形置放於概觀圖上，即可捲動工作流程設計工具，並變更編輯器的檢視。

> [!NOTE]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)] 使用者介面已視覺化。 活動設計工具只有在需要時才會呈現。 如果從未在設計工具介面上畫出工作流程的某部分，則該部分在概觀圖上會顯示為白色。 捲動概觀圖，即可完整畫出工作流程。

## <a name="copying-or-saving-workflows-as-images"></a>將工作流程複製或儲存成影像
 工作流程能夠以點陣圖格式複製，或儲存為點陣圖或向量格式。 複製或儲存影像提供一種匯出的方式，可將目前階層連結根目錄中的整個活動檢視匯出到其他程式，包含其子活動與所有展開的子活動。

 若要複製為影像，請以滑鼠右鍵按一下設計工具中的任何位置，然後選取 [**複製成影像**]。 若要儲存為影像，請以滑鼠右鍵按一下設計工具中的任何位置，然後選取 [**另存為影像**]。 工作流程可儲存為 JPG、PNG、GIF 或 XPS 格式。 在視窗底部的 [**另存新檔類型：** ] 下拉式清單方塊中，選取 [**另存**新檔] 對話方塊上的格式。

## <a name="fonts-and-colors"></a>字型和色彩
 在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 內的 [!INCLUDE[vs2010](../includes/vs2010-md.md)]中所使用的字型會受到環境字型所控制。 如果您的作業系統主題是高對比的色彩配置，[!INCLUDE[wfd2](../includes/wfd2-md.md)] 的顯示色彩就會變更。 變更字型或色彩設定後，必須重新啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]，[!INCLUDE[wfd2](../includes/wfd2-md.md)] 中的變更才會生效。