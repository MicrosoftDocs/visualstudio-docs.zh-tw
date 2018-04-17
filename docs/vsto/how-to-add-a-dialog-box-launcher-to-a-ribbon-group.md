---
title: 如何： 在功能區群組中加入對話方塊啟動 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d71124d0a3843053ad7558e0e1038b8d6626b5e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>如何：在功能區群組中加入對話方塊啟動程式
  您可以加入對話方塊啟動程式功能區上的任何群組。 對話方塊啟動是小型圖示出現在群組中。 使用者按一下此圖示以開啟相關的對話方塊或提供更多的選項與群組相關聯的工作窗格。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>在功能區群組中加入對話方塊啟動程式  
  
1.  在 [選取功能區程式碼檔案 （.vb 或.cs 檔案）**方案總管] 中**。  
  
2.  在**檢視**功能表上，按一下 **設計師**。  
  
3.  在功能區設計工具中，任何群組中，以滑鼠右鍵按一下，然後按一下**新增 DialogBoxLauncher**。  
  
     將程式碼加入<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>開啟自訂或內建對話方塊群組的事件。  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [如何： 將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何： 變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何： 自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何： 將控制項加入 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [自訂 Outlook 功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何： 顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說： 在執行階段更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  