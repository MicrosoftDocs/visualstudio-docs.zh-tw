---
title: "如何： 將控制項加入 Backstage 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7a58b9b59dd3625b3b9b7d8e9e3e77964eb0f2a5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>如何：將控制項加入至 Backstage 檢視
  您可以使用功能區設計工具將控制項加入後按一下開啟功能表**檔案** 索引標籤，當您執行應用程式中，您將加入的控制項**檔案**索引標籤會出現一個名為群組**增益集**。  
  
 您無法放置在控制項之前或之後內建控制項的 Visual Studio 中使用功能區設計工具。 內建控制項是已經出現在 Backstage 檢視的控制項。 如果您想要調整控制項的位置之前或內建控制項之後，您必須使用功能區 XML。 如需有關**功能區 (XML)**，請參閱[功能區 XML](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱[開發人員的 Office 2010 Backstage 檢視簡介](http://go.microsoft.com/fwlink/?LinkId=182189)和[自訂 Office 2010 Backstage 檢視適用於開發人員](http://go.microsoft.com/fwlink/?LinkId=182188)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>將控制項加入 Backstage 檢視  
  
1.  在設計檢視中開啟功能區項目。  
  
     如需如何新增**功能區 （視覺化設計工具）**至您的專案項目，請參閱[How to： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在 功能區設計工具中，按一下 **檔案** 索引標籤。  
  
     功能表的設計工具隨即出現。 這個設計介面不包含任何控制項。  
  
3.  從**Office 功能區控制項** 索引標籤**工具箱**，任何下列控制項拖曳至設計工具 功能表：  
  
    -   按鈕  
  
    -   核取方塊  
  
    -   組件庫  
  
    -   功能表  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  拖曳，將它們移至新的位置在功能表上的控制項。  
  
## <a name="see-also"></a>請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [如何： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  