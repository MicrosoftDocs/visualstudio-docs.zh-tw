---
title: 如何：檢視現有類型 (類別設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588703"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>如何：在類別設計工具中檢視現有類型

若要查看現有的類型及其成員，請將其圖案加入至類別圖。

您可以查看本機類型及參考類型。 本機類型存在目前已開啟的專案中，而且為可讀寫。 參考類型存在其他專案或參考組件中，而且為唯讀。

要在類別圖表上設計新類型，請參閱[如何：使用類設計器創建類型](how-to-create-types.md)。

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>在類別圖上查看專案中的類型

1. 從**解決方案資源管理器**中的專案中，打開現有的類圖 （.cd） 檔。 如果沒有類別圖，就將新的類別圖加入至專案。 請參閱[如何：將類別圖新增至專案](how-to-add-class-diagrams-to-projects.md)。

2. 從**解決方案資源管理器**中的專案中，將原始程式碼檔拖動到類別圖表。

    > [!NOTE]
    > 如果方案中有跨多個應用程式共用程式碼的專案，您只能從下列來源將檔案或程式碼拖曳至另一個類別圖：
    >
    > - 包含圖表的應用程式專案
    > - 由應用程式專案匯入的共用專案
    > - 參考的專案
    > - 組件

    代表原始程式碼檔中所定義類型的圖案就會出現在圖表上您拖曳檔案所至的位置。

還可以通過將一個或多個類型從**類視圖**中的專案節點拖動到類別圖表來查看專案中的類型。

> [!TIP]
> 如果**類視圖**未打開，則從 **"視圖"** 功能表打開**類視圖**。

要在關係圖上的預設位置顯示類型，請在**類視圖中**選擇一個或多個類型，按右鍵所選類型，然後選擇 **"查看類圖**"。

> [!NOTE]
> 如果專案中已有包含類型的已關閉類別圖，便會開啟類別圖以顯示類型圖案。 但是，如果專案中不存在包含該類型的類別圖表，**類設計器**將在專案中創建一個新的類別圖表，並打開它以顯示類型。

第一次在圖表上顯示類型時，類型圖案依預設會摺疊。 您可以展開圖案以檢視其內容。

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>在類別圖中顯示專案內容

在 **"解決方案資源管理器**"或 **"類視圖"** 中，按右鍵專案並選擇 **"視圖**"，然後選擇 **"查看類圖**"。 就會建立會自動填入內容的類別圖。

## <a name="see-also"></a>另請參閱

- [如何：檢視類型之間的繼承](how-to-view-inheritance-between-types.md)
- [如何：自訂類別圖表](how-to-customize-class-diagrams.md)
- [查看類型和關係](designing-and-viewing-classes-and-types.md)
