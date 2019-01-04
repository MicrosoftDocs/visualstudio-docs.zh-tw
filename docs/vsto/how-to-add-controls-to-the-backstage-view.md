---
title: 'HOW TO：將控制項加入至 Backstage 檢視 '
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6500118f775f9dfab75b615f28fab9e166a0104a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924653"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>HOW TO：將控制項加入至 Backstage 檢視
  您可以使用功能區設計工具將控制項新增至後按一下開啟功能表**檔案** 索引標籤。當您執行應用程式中，您將加入的控制項**檔案**索引標籤會出現一個名為群組**增益集**。  
  
 您無法在 Visual Studio 中使用功能區設計工具內建控制項之前或之後放置控制項。 內建控制項是已經出現在 Backstage 檢視的控制項。 如果您想要調整控制項的位置，內建控制項之前或之後，您必須使用功能區 XML。 如需詳細資訊**功能區 (XML)**，請參閱[功能區 XML](../vsto/ribbon-xml.md)。 如需自訂 Backstage 檢視的詳細資訊，請參閱 <<c0> [ 開發人員的 Office 2010 Backstage 檢視簡介](http://go.microsoft.com/fwlink/?LinkId=182189)並[來自訂開發人員的 Office 2010 Backstage 檢視](http://go.microsoft.com/fwlink/?LinkId=182188)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>將控制項加入至 Backstage 檢視  
  
1.  在 [設計] 檢視中開啟功能區項目。  
  
     如需如何新增**功能區 （視覺化設計工具）** 至您的專案項目，請參閱[How to:開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在 [功能區設計工具中，按一下**檔案**] 索引標籤。  
  
     功能表設計工具隨即出現。 此設計介面不包含任何控制項。  
  
3.  從**Office 功能區控制項**索引標籤**工具箱**，任何下列控制項拖曳至設計工具 功能表：  
  
    -   按鈕  
  
    -   核取方塊  
  
    -   Gallery  
  
    -   功能表  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  拖曳控制項，以在功能表上將它們移至新位置。  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
