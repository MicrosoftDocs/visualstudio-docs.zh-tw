---
title: 工作流程設計工具-工作流程設計工具中的鍵盤快速鍵
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83664d6402c23da89adf332bc9cd34eac89384bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977640"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>工作流程設計中的鍵盤快速鍵

所有核心功能的 Windows 工作流程設計工具可以利用鍵盤存取。

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>使用鍵盤巡覽工作流程設計工具

在 Visual Studio 2010、 內部，全域快速鍵與除錯快速鍵套用到工作流程設計工具。 此外，已建立的工作流程設計工具特定的鍵盤快速鍵的數字。 在 Visual Studio 2010 中，所有的鍵盤快速鍵可以重新對應。 然而，在重新裝載的應用程式中，這些快速鍵都已硬式編碼。

### <a name="workflow-designer-keyboard-shortcuts"></a>工作流程設計工具快速鍵

下表摘要說明指派給工作流程設計工具命令的預設鍵盤快速鍵。

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

下列是透過鍵盤建構流程圖所使用的手勢。 與工作流程設計工具的其餘部分，活動會加入至設計工具介面提供與 Visual Studio 2010 的全域工具箱快速鍵。

- 若要移動活動，請選取該活動並使用方向鍵重新定位。

- 若要調整流程圖的大小，請使用方向鍵將活動移出流程圖目前的框線外。 流程圖會自動調整大小。

- 若要設定某個活動做為開始節點，使用**Set as StartNode**內容功能表中的命令。

- 若要連接活動：

    1.  使用 Tab 鍵選取來源活動。

    2.  視需要按幾次 CTRL+E、M，將鍵盤焦點移至目的地活動。

    3.  按 CTRL+E、S 將目的地活動加入至選取範圍。

    4.  按 CTRL+E、F 加入從來源到目的地的連接線。

有關使用鍵盤連接活動的附註：

- 只要先加入更多活動至選取範圍，再按 CTRL+E、F，就可以同時做多個連接。連接會以活動加入至選取範圍的順序來做。

- 如果成對的活動無法連接，例如來源活動已經有傳出的連接，則選取範圍內活動之間的其他連接，只要有可能連接仍然會連接。

- 當**FlowDecision**包含在選取項目和**FlowDecision**沒有傳出的連接時，連接線會放在**True**分支。

### <a name="expression-editing"></a>運算式編輯

根據預設，Visual Basic 文字編輯的預設鍵盤快速鍵適用於內部運算式編輯器，在工作流程設計工具，但有下列限制：

- 下列命令的快速鍵重新對應將不會有任何作用。 編輯運算式時，您只能使用預設的快速鍵存取這些命令。

   - 剪下
   - 複製
   - 貼上
   - 全選
   - 復原
   - 取消復原

- 若要重新對應 Visual Studio 2010 中的工作流程設計工具內的運算式編輯命令的鍵盤快速鍵，編輯工作流程設計工具範圍中的快速鍵。 在文字編輯器 範圍內所做的變更會自動不適用於工作流程設計工具。 如果兩個地方的快速鍵都要重新對應，您必須套用這些變更兩次 (兩個範圍各一次)。