---
title: "如何： 將功能區設計工具功能區匯出至功能區 XML |Microsoft 文件"
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
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b73bff8170e351e9e22e95d53ae446895cfdbd2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>如何：將功能區設計工具的功能區匯出到功能區 XML
  **功能區 （視覺化設計工具）**項目不支援所有可能的功能區自訂類型。 若要進階方式自訂功能區，您可以從設計工具的功能區匯出至功能區 XML，並直接編輯 XML。  
  
> [!NOTE]  
>  並非所有的屬性值會出現在功能區 XML 檔案。 如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>若要將功能區設計工具功能區匯出至功能區 XML  
  
1.  以滑鼠右鍵按一下功能區程式碼檔案中的**方案總管] 中**，然後按一下 [**檢視表設計工具**。  
  
2.  功能區設計工具中，以滑鼠右鍵按一下，然後按一下 **功能區匯出至 XML**。  
  
     Visual Studio 會將功能區 XML 檔案和功能區 XML 程式碼檔案加入至您的專案。  
  
3.  在功能區程式碼類別中，找出開頭的註解`TODO:`。  
  
4.  在這些註解，以複製程式碼區塊**ThisAddin**， **ThisWorkbook**，或**ThisDocument**類別，根據您所開發的方案類型。  
  
     此程式碼可讓 Microsoft Office 應用程式探索和載入自訂功能區。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。  
  
5.  在**ThisAddin**， **ThisWorkbook**，或**ThisDocument**類別，請取消註解的程式碼區塊。  
  
     您取消註解程式碼之後，它應該類似下列的範例。 在此範例中，功能區類別稱為`MyRibbon`。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  切換至 功能區 XML 程式碼檔案，並尋找`Ribbon Callbacks`區域。  
  
     這是您用來撰寫以處理使用者動作，例如按一下按鈕的回呼方法。  
  
7.  建立回呼方法，以便您在功能區設計工具程式碼撰寫每個事件處理常式。  
  
8.  所有事件處理常式程式碼的事件處理常式回呼方法，並修改程式碼以使用功能區擴充功能 (RibbonX) 程式設計模型。  
  
     如需撰寫回呼方法與使用 RibbonX 程式設計模型的資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說： 使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  