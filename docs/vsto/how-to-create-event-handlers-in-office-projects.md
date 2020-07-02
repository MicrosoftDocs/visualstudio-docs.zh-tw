---
title: 如何：在 Office 專案中建立事件處理常式
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ee85d89dcb990cebd595dadbd7b28add4a7b371a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538303"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>如何：在 Office 專案中建立事件處理常式
  有數種方式可以在 Visual Basic 和 c # 中建立事件處理常式。 在設計檢視中，您可以按兩下控制項來建立控制項的預設事件處理常式，或使用 [**屬性**] 視窗的 [事件] 窗格，針對控制項上的任何事件建立處理常式。 不過，如果您是在程式碼視圖中，您可能不想要切換到設計檢視來建立事件處理常式。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>若要在 Visual Basic 中建立事件處理常式

1. 從程式碼編輯器頂端的 [**類別名稱**] 下拉式清單中，選取您想要為其建立事件處理常式的物件。

    > [!NOTE]
    > 如果您想要建立或的事件處理常式 `ThisDocument` `ThisWorkbook` ，則必須在 [**類別名稱**] 下拉式清單中選取 **[（ThisDocument 事件）** ] 或 **（ThisWorkbook 事件）**

2. 從程式碼編輯器頂端的 [**方法名稱**] 下拉式清單中，選取事件。

     Visual Studio 會建立事件處理常式，並將插入點移至新建立的事件處理常式。 如果事件處理常式已經存在，插入點就會移至現有的事件處理常式。

### <a name="to-create-an-event-handler-in-c"></a>若要在 C 中建立事件處理常式\#

1. 在類別的**啟動**事件中建立事件委派，方法是輸入限定的事件名稱後面接著一個空格，然後再輸入， **+=** 之後不加空格。 例如：

     `this.<object name>.<event name> +=`

2. 在程式程式碼的結尾，按兩次 TAB 鍵。

     Visual Studio 會自動完成程式程式碼、建立事件處理常式，並將插入點移至新建立的事件處理常式。

## <a name="see-also"></a>另請參閱
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [組建 Office 方案](../vsto/building-office-solutions.md)
