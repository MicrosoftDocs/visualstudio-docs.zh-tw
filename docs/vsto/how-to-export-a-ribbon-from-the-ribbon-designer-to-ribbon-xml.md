---
title: 如何：將功能區設計工具的功能區匯出至功能區 XML
description: 瞭解自訂功能區時，您可以從設計工具將功能區匯出至功能區 XML，並直接編輯 XML。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a0511fd103345859f96b18f333465106505057a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953977"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>如何：將功能區設計工具的功能區匯出至功能區 XML
  **功能區 (的視覺化設計工具)** 專案不支援所有可能的功能區自訂類型。 若要以先進的方式自訂功能區，您可以從設計工具將功能區匯出至功能區 XML，並直接編輯 XML。

> [!NOTE]
> 並非所有的屬性值都會出現在功能區 XML 檔案中。 如需詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>將功能區設計工具的功能區匯出至功能區 XML

1. 以滑鼠右鍵按一下 **方案總管** 中的功能區程式碼檔案，然後按一下 [ **視圖設計** 工具]。

2. 以滑鼠右鍵按一下 [功能區設計工具]，然後按一下 [ **將功能區匯出到 XML**]。

     Visual Studio 將功能區 XML 檔案和功能區 XML 程式碼檔案加入至您的專案。

3. 在功能區程式碼類別中，找出以開頭的批註 `TODO:` 。

4. 將這些批註中的程式碼區塊複製到 **ThisAddin**、 **ThisWorkbook** 或 **ThisDocument** 類別，視您開發的方案類型而定。

     這段程式碼可讓 Microsoft Office 應用程式探索和載入您的自訂功能區。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。

5. 在 **ThisAddin**、 **ThisWorkbook** 或 **ThisDocument** 類別中，取消批註程式碼區塊。

     在您取消批註程式碼之後，它應該會類似下列範例。 在此範例中，會呼叫功能區類別 `MyRibbon` 。

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. 切換至功能區 XML 程式碼檔案，並尋找 `Ribbon Callbacks` 區域。

     您可以在這裡撰寫回呼方法來處理使用者動作，例如按一下按鈕。

7. 針對您在功能區設計工具程式碼中撰寫的每個事件處理常式建立回呼方法。

8. 將事件處理常式的所有事件處理常式程式碼移至回呼方法，並修改程式碼以使用功能區擴充性 (RibbonX) 程式設計模型。

     如需撰寫回呼方法和使用 RibbonX 程式設計模型的相關資訊，請參閱 [功能區 XML](../vsto/ribbon-xml.md)。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [逐步解說：使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
