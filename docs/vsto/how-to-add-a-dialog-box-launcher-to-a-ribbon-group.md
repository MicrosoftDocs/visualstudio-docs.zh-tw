---
title: 作法：將對話方塊啟動器加入至功能區群組
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
ms.openlocfilehash: b930348845e04dca089cf153a11cc2a9fd29c880
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255897"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>作法：將對話方塊啟動器加入至功能區群組
  您可以將對話方塊啟動器加入至功能區上的任何群組。 對話方塊啟動器是出現在群組中的小型圖示。 使用者按一下此圖示，即可開啟相關的對話方塊或工作窗格，以提供與群組相關的更多選項。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>將對話方塊啟動器加入至功能區群組

1. 在**方案總管**中選取功能區程式碼檔案（ *.vb*或 *.cs*檔案）。

2. 在 [ **View** ] 功能表上，按一下 [**設計師**]。

3. 在功能區設計工具中，以滑鼠右鍵按一下任何群組，然後按一下 [**加入 DialogBoxLauncher**]。

     將程式碼加入<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>至群組的事件，以開啟自訂或內建對話方塊。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [如何：從功能區設計工具將功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：變更功能區上索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項新增至 backstage 視圖](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：在執行時間更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [逐步解說：使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
