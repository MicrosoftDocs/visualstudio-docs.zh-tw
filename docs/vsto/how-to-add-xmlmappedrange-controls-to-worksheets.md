---
title: 如何：將 XMLMappedRange 控制項加入至工作表
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544881"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>如何：將 XMLMappedRange 控制項加入至工作表
  當您將 XML 元素對應至 Microsoft Office Excel 中的資料格時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項加入至工作表。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>控制項無法在 [**工具箱**] 或 [**資料來源**] 視窗中使用。 此外，您也無法 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 以程式設計方式建立控制項。

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>若要將 XMLMappedRange 控制項加入至工作表

1. 在 Visual Studio 設計工具中開啟 Excel 活頁簿。

2. 開啟您要加入控制項的工作表。

3. 在 [**開發人員**] 索引標籤上，按一下 [**來源**]。

    > [!NOTE]
    > 如果 [**開發人員**] 索引標籤在功能區中看不到，您必須啟用它。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

     [ **XML 來源**] 工作窗格隨即出現。

4. 在 [ **Xml 來源**] 工作窗格中，按一下 [ **xml 對應**]。

5. 在 [ **XML 對應**] 對話方塊中，按一下 [**加入**]。

     [ **XML 來源**] 對話方塊隨即出現。

6. 從 [ **Xml 來源**] 對話方塊中選取 [xml 架構]，然後按一下 [**開啟**]。

     架構就會加入至 [ **XML 對應**] 對話方塊。

7. 在 [ **XML 對應**] 對話方塊中，按一下 **[確定]**。

8. 將專案從 [ **XML 來源**] 工作窗格拖曳至工作表上的儲存格。

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>隨即建立，並加入至專案。

    > [!NOTE]
    > 如果您從 [ **XML 來源**] 工作窗格拖曳父元素， <xref:Microsoft.Office.Tools.Excel.ListObject> 就會建立控制項。

## <a name="see-also"></a>另請參閱
- [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
