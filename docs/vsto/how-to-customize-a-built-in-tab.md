---
title: 如何： 自訂內建索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1343ee966d63b0ddc74bf1e18cbbe8bd6d476a0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-a-built-in-tab"></a>如何：自訂內建索引標籤
  您可在內建索引標籤加入群組和控制項。內建索引標籤是已位在 Microsoft Office 應用程式功能區的索引標籤。 例如，**資料** 索引標籤是在 Excel 中的內建索引標籤。 當您建立自訂群組時，它會出現在索引標籤的最末端，但是您可以在索引標籤上任意移動群組。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  您可以在內建索引標籤加入群組，但無法從內建索引標籤移除內建群組。  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>在內建索引標籤加入群組  
  
1.  以滑鼠右鍵按一下功能區程式碼檔案中的**方案總管] 中**，然後按一下 [**檢視表設計工具**。  
  
    > [!NOTE]  
    >  如果未出現功能區程式碼檔案，在**方案總管 中**，您必須新增**功能區項目**至您的專案。 請參閱[How to： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在功能區設計工具中，任何索引標籤上按一下滑鼠右鍵，然後按一下**屬性**。  
  
3.  在**屬性**視窗中，展開  **ControlId**屬性，並將其設定**ControlIdType**屬性**Office**。  
  
4.  設定**OfficeId**屬性*控制項 ID*您想要自訂內建索引標籤。  
  
     控制項 ID 是唯一識別 Microsoft Office 應用程式內建索引標籤、群組和控制項的名稱。  
  
     如需控制項 Id 的清單，請參閱[Office 2010 說明檔： Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
5.  從**Office 功能區控制項** 索引標籤**工具箱**，將群組拖曳至  索引標籤。  
  
    > [!NOTE]  
    >  內建群組不會顯示在設計工具中。 因此，若要判斷是否會使用內建索引標籤的唯一方式是檢查**ControlId**  索引標籤的屬性。  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>將群組放置在內建索引標籤  
  
1.  在功能區設計工具中，選取自訂群組。  
  
2.  在**屬性**視窗中，展開 **位置**屬性。  
  
3.  設定**PositionType**屬性設為適當值：  
  
    -   **BeforeOfficeId**置於指定的內建群組之前的群組。  
  
    -   **AfterOfficeId**將群組放置在指定的內建群組之後。  
  
4.  設定**OfficeId**內建群組的控制項 ID 的屬性。  
  
     如需控制項 Id 的清單，請參閱[Office 2010 說明檔： Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說： 使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [如何： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何： 變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何： 將控制項加入 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  