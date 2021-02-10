---
title: 如何：檢視現有類型 (類別設計工具)
description: 瞭解如何將其圖形加入至類別圖，以查看現有的類型及其成員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5249102013aaf72a48c7137b415636952ed1d0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951806"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>如何：在類別設計工具中檢視現有類型

若要查看現有的類型及其成員，請將其圖案加入至類別圖。

您可以查看本機類型及參考類型。 本機類型存在目前已開啟的專案中，而且為可讀寫。 參考類型存在其他專案或參考組件中，而且為唯讀。

若要在類別圖上設計新的類型，請參閱 [如何：使用類別設計工具建立類型](how-to-create-types.md)。

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>在類別圖上查看專案中的類型

1. 從 **方案總管** 中的專案，開啟現有的類別圖表 ( .cd) 檔。 如果沒有類別圖，就將新的類別圖加入至專案。 請參閱[如何：將類別圖新增至專案](how-to-add-class-diagrams-to-projects.md)。

2. 從 **方案總管** 中的專案，將原始程式碼檔拖曳至類別圖。

    > [!NOTE]
    > 如果方案中有跨多個應用程式共用程式碼的專案，您只能從下列來源將檔案或程式碼拖曳至另一個類別圖：
    >
    > - 包含圖表的應用程式專案
    > - 由應用程式專案匯入的共用專案
    > - 參考的專案
    > - 組件

    代表原始程式碼檔中所定義類型的圖案就會出現在圖表上您拖曳檔案所至的位置。

您也可以從 **類別檢視** 中的專案節點，將一或多個類型拖曳至類別圖表，以查看專案中的類型。

> [!TIP]
> 如果 **類別檢視** 未開啟，請從 [ **View** ] 功能表開啟 **類別檢視**。

若要在圖表上的預設位置顯示類型，請在 [ **類別檢視** 中選取一或多個類型，以滑鼠右鍵按一下選取的類型，然後選擇 [ **視圖類別圖**]。

> [!NOTE]
> 如果專案中已有包含類型的已關閉類別圖，便會開啟類別圖以顯示類型圖案。 但是，如果專案中沒有包含類型的類別圖表， **類別設計工具** 會在專案中建立新的類別圖表，並開啟該圖表以顯示類型。

第一次在圖表上顯示類型時，類型圖案依預設會摺疊。 您可以展開圖案以檢視其內容。

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>在類別圖中顯示專案內容

在 **方案總管** 或 **類別檢視** 中，以滑鼠右鍵按一下專案，然後選擇 [ **視圖**]，再選擇 [ **視圖類別圖**]。 就會建立會自動填入內容的類別圖。

## <a name="see-also"></a>另請參閱

- [如何：檢視類型之間的繼承](how-to-view-inheritance-between-types.md)
- [如何：自訂類別圖表](how-to-customize-class-diagrams.md)
- [檢視類型和關聯性](designing-and-viewing-classes-and-types.md)
