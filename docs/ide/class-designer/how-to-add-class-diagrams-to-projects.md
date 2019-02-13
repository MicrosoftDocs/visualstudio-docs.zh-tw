---
title: HOW TO：將類別圖表新增至專案 (類別設計工具)
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26ac40b3ae84aad689df9884ad8453860f91d971
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919712"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>HOW TO：將類別圖表新增至專案

若要設計、編輯和重構類別及其他類型，請將類別圖加入至 C#、Visual Basic 或 C++ 專案。 若要在專案中視覺化程式碼的不同部分，請將多個類別圖加入至專案。

您不能從跨多個應用程式共用程式碼的專案建立類別圖。 若要建立 UML 類別圖表，請參閱[建立 UML 模組化專案和圖表](../../modeling/create-uml-modeling-projects-and-diagrams.md)。

## <a name="install-the-class-designer-component"></a>安裝類別設計工具元件

若您執行 Visual Studio 2017 而未安裝**類別設計工具**元件，請遵循下列步驟加以安裝。

1. 從 Windows [開始] 功能表開啟 **Visual Studio 安裝程式**，或從 Visual Studio 的功能表列選取 [工具] > [取得工具與功能]。

   **Visual Studio 安裝程式**隨即開啟。

1. 選取 [個別元件] 索引標籤，然後向下捲動到 [程式碼工具] 分類。

1. 選取 [類別設計工具]，然後選取 [修改]。

   ![Visual Studio 安裝程式中的類別設計工具元件](media/class-designer-component.png)

   **類別設計工具**元件會開始安裝。

## <a name="add-a-blank-class-diagram-to-a-project"></a>將空白類別圖表新增至專案

1. 在**方案總管**中，以滑鼠右鍵按一下專案節點，然後選擇 [新增] > [新增項目]。 或者按 **Ctrl**+**Shift**+**A**。

   [新增項目] 對話方塊隨即開啟。

2. 展開 [常用項目] > [一般]，然後從範本清單中選取 [類別圖表]。 若是 Visual C++ 專案，請在 [公用程式] 分類中尋找**類別圖表**範本。

   > [!NOTE]
   > 若您沒有看到**類別圖表**範本，請[遵循這些步驟](#install-the-class-designer-component)安裝 Visual Studio 的**類別設計工具**元件。

   類別圖表會在類別設計工具中開啟，並在**方案總管**中顯示為副檔名為 *.cd* 的檔案。 您可以從 [工具箱] 將圖形和線條拖曳到圖表。

若要加入多個類別圖，請重複本程序的步驟。

## <a name="add-a-class-diagram-based-on-existing-types"></a>根據現有類型新增類別圖表

在 [方案總管] 中，開啟類別檔案的快顯功能表 (以滑鼠右鍵按一下)，然後選擇 [檢視類別圖表]。

-或-

在 [類別檢視] 中，開啟命名空間或類型操作功能表，然後選擇 [檢視類別圖表]。

> [!TIP]
> 如果未開啟 [類別檢視]，請從 [檢視] 功能表開啟 [類別檢視]。

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>在類別圖表中顯示完整專案的內容

在 [方案總管] 或 [類別檢視] 中，在專案上按一下滑鼠右鍵並選擇 [檢視]，然後選擇 [類別圖表檢視]。

就會建立會自動填入內容的類別圖表。

## <a name="see-also"></a>另請參閱

- [如何：使用 [類別設計工具] 建立類型](how-to-create-types.md)
- [如何：檢視現有類型](how-to-view-existing-types.md)
- [設計和檢視類別及類型](designing-and-viewing-classes-and-types.md)
