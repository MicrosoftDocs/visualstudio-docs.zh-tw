---
title: 鍵盤快速鍵，在工作流程設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a03463d292fa1d4d980c62daa74b291d6a8cb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951953"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>工作流程設計中的鍵盤快速鍵
[!INCLUDE[wfd1](../includes/wfd1-md.md)] 的所有核心功能都可以利用鍵盤存取。  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>使用鍵盤巡覽工作流程設計工具  
 在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 內部，全域快速鍵與除錯快速鍵適用於 [!INCLUDE[wfd2](../includes/wfd2-md.md)]。 此外，也建立了幾個 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 專用的快速鍵。 在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中，所有的快速鍵都可以重新對應。 然而，在重新裝載的應用程式中，這些快速鍵都已硬式編碼。  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>工作流程設計工具快速鍵  
 下表摘要說明指派給 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 命令的快速鍵。  
  
|快速鍵|用途|  
|--------------|-------------|  
|CTRL+E、A|顯示或隱藏引數設計工具。|  
|CTRL+E、C|將選取活動原地摺疊。|  
|CTRL+E、E|將選取活動原地展開。|  
|CTRL+E、F|將流程圖中的選取活動連接起來。|  
|CTRL+E、I|顯示或隱藏匯入設計工具。|  
|CTRL+E、M|將鍵盤焦點移至定位順序中的下一個項目。|  
|CTRL+E、N|在選取活動 (或最接近者) 的範圍內建立新的變數。|  
|CTRL+E、O|顯示或隱藏概觀圖。|  
|CTRL+E、P|巡覽至所選活動的父系。 這會使階層連結巡覽上移一層，也會變更設計工具介面上的根活動。|  
|CTRL+E、S|將含有鍵盤焦點的項目加入至目前的選取範圍。|  
|CTRL+E、V|顯示或隱藏變數設計工具。|  
|CTRL+E、X|展開工作流程中的所有活動。|  
|CTRL+ALT+F6|將鍵盤焦點從目前的 UI 區域移至順序中的下一個區域。 順序如下：<br /><br /> 1.階層連結巡覽列<br />2.設計工具介面<br />3.引數/變數/匯入設計工具 (如果已開啟)<br />4.Shell|  
  
### <a name="flowchart"></a>流程圖  
 下列是透過鍵盤建構流程圖所使用的手勢。 就像在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 的其餘部分，活動會使用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 提供的全域工具箱快速鍵加入至設計工具介面。  
  
- 若要移動活動，請選取該活動並使用方向鍵重新定位。  
  
- 若要調整流程圖的大小，請使用方向鍵將活動移出流程圖目前的框線外。 流程圖會自動調整大小。  
  
- 若要將活動設為 [啟動] 節點中，使用**Set as StartNode**的內容功能表命令。  
  
- 若要連接活動：  
  
  1. 使用 Tab 鍵選取來源活動。  
  
  2. 視需要按幾次 CTRL+E、M，將鍵盤焦點移至目的地活動。  
  
  3. 按 CTRL+E、S 將目的地活動加入至選取範圍。  
  
  4. 按 CTRL+E、F 加入從來源到目的地的連接線。  
  
  有關使用鍵盤連接活動的附註：  
  
- 只要先加入更多活動至選取範圍，再按 CTRL+E、F，就可以同時做多個連接。連接會以活動加入至選取範圍的順序來做。  
  
- 如果成對的活動無法連接，例如來源活動已經有傳出的連接，則選取範圍內活動之間的其他連接，只要有可能連接仍然會連接。  
  
- 當**FlowDecision**包含在選取項目和**FlowDecision**沒有傳出的連接器，連接器會放在 **，則為 True**分支。  
  
### <a name="expression-editing"></a>運算式編輯  
 根據預設，[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 文字編輯的預設快速鍵適用於 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中的運算式編輯器內部，並有下列限制：  
  
- 下列命令的快速鍵重新對應將不會有任何作用。 編輯運算式時，您只能使用預設的快速鍵存取這些命令。  
  
    1. 剪下  
  
    2. 複製  
  
    3. 貼上  
  
    4. 全選  
  
    5. 復原  
  
    6. 取消復原  
  
- 若要重新對應 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 內部的運算式編輯命令快速鍵，請在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 範圍內編輯快速鍵。 在 [文字編輯器] 範圍內所做的變更，不會自動套用到 [!INCLUDE[wfd2](../includes/wfd2-md.md)]。 如果兩個地方的快速鍵都要重新對應，您必須套用這些變更兩次 (兩個範圍各一次)。