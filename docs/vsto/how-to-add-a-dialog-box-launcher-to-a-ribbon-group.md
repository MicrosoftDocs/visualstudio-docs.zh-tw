---
title: HOW TO：在功能區群組中新增對話方塊啟動器
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d831cb629665e641394d011bd11eb74481c4f94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826440"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>HOW TO：在功能區群組中新增對話方塊啟動器
  您可以加入功能區上的任何群組的對話方塊啟動器。 對話方塊啟動器是群組中顯示的小圖示。 使用者按一下此圖示以開啟相關的對話方塊或提供更多的選項與群組相關的工作窗格。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>若要在功能區群組中新增對話方塊啟動器

1. 選取 [功能區程式碼檔案 (*.vb*或是 *.cs*檔案) 中**方案總管] 中**。

2. 在 **檢視**功能表上，按一下**設計師**。

3. 在 功能區設計工具中，以滑鼠右鍵按一下任何群組，然後**加入 DialogBoxLauncher**。

     將程式碼加入<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>的群組，以開啟 自訂或內建的對話方塊中的事件。

## <a name="see-also"></a>另請參閱
- [功能區概觀](../vsto/ribbon-overview.md)
- [在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [如何：將功能區匯出至功能區 XML 功能區設計工具](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項加入至 backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [適用於 Outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
- [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：更新在執行階段的功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
