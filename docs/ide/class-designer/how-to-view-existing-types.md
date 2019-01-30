---
title: HOW TO：檢視現有類型 (類別設計工具)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb594bd1096dbf2908ed2daa21706f60d329264e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038353"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>HOW TO：在 [類別設計工具] 中檢視現有類型

若要查看現有的類型及其成員，請將其圖案加入至類別圖。

您可以查看本機類型及參考類型。 本機類型存在目前已開啟的專案中，而且為可讀寫。 參考類型存在其他專案或參考組件中，而且為唯讀。

若要在類別圖上設計新的類型，請參閱[如何：使用 [類別設計工具] 建立類型](how-to-create-types.md)。

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>在類別圖上查看專案中的類型

1.  從 [方案總管] 的專案中開啟現有的類別圖表 (.cd) 檔案。 如果沒有類別圖，就將新的類別圖加入至專案。 請參閱[如何：將類別圖表新增至專案](how-to-add-class-diagrams-to-projects.md)。

2.  將原始程式碼檔從 [方案總管] 的專案拖曳至類別圖表。

    > [!NOTE]
    > 如果方案中有跨多個應用程式共用程式碼的專案，您只能從下列來源將檔案或程式碼拖曳至另一個類別圖：
    >
    > - 包含圖表的應用程式專案
    > - 由應用程式專案匯入的共用專案
    > - 參考的專案
    > - 組件

    代表原始程式碼檔中所定義類型的圖案就會出現在圖表上您拖曳檔案所至的位置。

您也可以將一或多個類型從 [類別檢視] 的專案節點中拖曳至類別圖表，以檢視專案中的類型。

> [!TIP]
> 如果未開啟 [類別檢視]，請從 [檢視] 功能表開啟 [類別檢視]。

若要在圖表上的預設位置顯示類型，請在 [類別檢視] 中選取一或多個類型、在所選類型上按一下滑鼠右鍵，並且選擇 [檢視類別圖表]。

> [!NOTE]
> 如果專案中已有包含類型的已關閉類別圖，便會開啟類別圖以顯示類型圖案。 但是，如果專案中沒有包含類型的類別圖表，[類別設計工具] 會在專案中建立新的類別圖表，並且開啟圖表以顯示類型。

第一次在圖表上顯示類型時，類型圖案依預設會摺疊。 您可以展開圖案以檢視其內容。

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>在類別圖中顯示專案內容

在 [方案總管] 或 [類別檢視] 中，在專案上按一下滑鼠右鍵並選擇 [檢視]，然後選擇 [類別圖表檢視]。 就會建立會自動填入內容的類別圖。

## <a name="see-also"></a>另請參閱

- [如何：檢視類型之間的繼承](how-to-view-inheritance-between-types.md)
- [如何：自訂類別圖表](how-to-customize-class-diagrams.md)
- [檢視類型與關聯性](designing-and-viewing-classes-and-types.md)