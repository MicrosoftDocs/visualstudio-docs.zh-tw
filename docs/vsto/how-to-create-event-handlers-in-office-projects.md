---
title: HOW TO：建立 Office 專案中的事件處理常式
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 537bae766b71744a61e5158b1a859cade4cdcda7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419644"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>HOW TO：建立 Office 專案中的事件處理常式
  有數種方式可在 Visual Basic 和 C# 中建立事件處理常式。 在 [設計] 檢視中，您可以建立預設控制項事件處理常式，方法是按兩下控制項，或使用的 [事件] 窗格**屬性**視窗建立控制項上的任何事件處理常式。 不過，如果您是在程式碼檢視中，您可能不想要切換至 [設計] 檢視中建立事件處理常式。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>若要在 Visual Basic 中建立事件處理常式

1. 從**類別名稱**的程式碼編輯器頂端的下拉式清單，選取您想要的物件建立的事件處理常式。

    > [!NOTE]
    > 如果您想要建立事件處理常式`ThisDocument`或`ThisWorkbook`，您必須選取 **（ThisDocument 事件）** 或是 **（ThisWorkbook 事件）** 中**類別名稱**下拉式清單

2. 從**方法名稱**下拉式清單在上方的程式碼編輯器中，選取 事件。

     Visual Studio 建立的事件處理常式，並將插入點移至新建立的事件處理常式。 如果事件處理常式已經存在，將插入點移到現有的事件處理常式。

### <a name="to-create-an-event-handler-in-c"></a>在 C 中建立事件處理常式\#

1. 建立中的事件委派**啟始**輸入完整的事件名稱，後面接著空格，然後再輸入類別的事件 **+=** 之後沒有空格。 例如:

     `this.<object name>.<event name> +=`

2. 在下一行程式碼結束時，再按兩次 TAB 鍵。

     Visual Studio 會自動完成程式碼行，建立事件處理常式中，並將插入點移至新建立的事件處理常式。

## <a name="see-also"></a>另請參閱
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [建置 Office 方案](../vsto/building-office-solutions.md)
