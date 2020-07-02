---
title: 如何：將類別圖表加入至專案 (類別設計工具)
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a54b01f718c2faab8d36cc8e44805707fd0cc35f
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771030"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>如何：將類別圖表新增到專案

若要設計、編輯和重構類別及其他類型，請將類別圖加入至 C#、Visual Basic 或 C++ 專案。 若要在專案中視覺化程式碼的不同部分，請將多個類別圖加入至專案。

您不能從跨多個應用程式共用程式碼的專案建立類別圖。 若要建立 UML 類別圖表，請參閱[建立 UML 模組化專案和圖表](../../modeling/what-s-new-for-design-in-visual-studio.md)。

## <a name="install-the-class-designer-component"></a>安裝類別設計工具元件

若您尚未安裝**類別設計工具**元件，請遵循下列步驟安裝。

1. 從 Windows [開始] 功能表開啟 **Visual Studio 安裝程式**，或從 Visual Studio 的功能表列選取 [工具]**** > [取得工具與功能]****。

   **Visual Studio 安裝程式**隨即開啟。

1. 選取 [個別元件]**** 索引標籤，然後向下捲動到 [程式碼工具]**** 分類。

1. 選取 [類別設計工具]****，然後選取 [修改]****。

   ![Visual Studio 安裝程式中的類別設計工具元件](media/class-designer-component.png)

   **類別設計工具**元件會開始安裝。

## <a name="add-a-blank-class-diagram-to-a-project"></a>將空白類別圖表新增至專案

1. 在**方案總管**中，以滑鼠右鍵按一下專案節點，然後選擇 [新增]**** > [新增項目]****。 或者，按**Ctrl** + **Shift** + **A**。

   [**加入新專案**] 對話方塊隨即開啟。

2. 展開 [**通用專案**]  >  **[一般**]，然後從範本清單中選取 [**類別圖表**]。 若是 Visual C++ 專案，請在 [公用程式]**** 分類中尋找**類別圖表**範本。

   > [!NOTE]
   > 若您沒有看到**類別圖表**範本，請[遵循這些步驟](#install-the-class-designer-component)安裝 Visual Studio 的**類別設計工具**元件。

   類別圖表會在類別設計工具中開啟，並在**方案總管**中顯示為副檔名為 *.cd* 的檔案。 您可以從 [工具箱]**** 將圖形和線條拖曳到圖表。

若要加入多個類別圖，請重複本程序的步驟。

## <a name="add-a-class-diagram-based-on-existing-types"></a>根據現有類型新增類別圖表

在 [方案總管]**** 中，開啟類別檔案的快顯功能表 (以滑鼠右鍵按一下)，然後選擇 [檢視類別圖表]****。

-或-

在 [類別檢視]**** 中，開啟命名空間或類型操作功能表，然後選擇 [檢視類別圖表]****。

> [!TIP]
> 如果**類別檢視**未開啟，請從 [ **View** ] 功能表開啟**類別檢視**。

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>在類別圖表中顯示完整專案的內容

在**方案總管**或類別檢視中，以滑鼠右鍵按一下專案，然後選擇 [**視圖**]，再選擇 [**視圖類別圖表**]。

就會建立會自動填入內容的類別圖表。

> [!NOTE]
> 類別設計工具尚無法於 .NET Core 專案中使用。

## <a name="see-also"></a>另請參閱

- [如何：使用類別設計工具建立類型](how-to-create-types.md)
- [如何：查看現有的類型](how-to-view-existing-types.md)
- [設計和視圖類別和類型](designing-and-viewing-classes-and-types.md)
