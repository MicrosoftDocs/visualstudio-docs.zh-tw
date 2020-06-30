---
title: 如何：將架構對應至 Visual Studio 內的工作表
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538134"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>如何：將架構對應至 Visual Studio 內的工作表
  在 Visual Studio 中開啟工作表時，您可以將 XML 架構對應至工作表。 當活頁簿在 Visual Studio 外開啟時，您會使用與您所使用的相同 Microsoft Office Excel 工具。 無論您是在建立 Excel 方案之前或之後，將架構對應至工作表，Office 專案都會建立相同的物件。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> 您不能在 Excel 方案中使用多部分 XML 架構。

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>若要在 Visual Studio 中將 XML 架構對應至 Excel 工作表

1. 在 Visual Studio 內開啟 Excel 活頁簿或範本專案。

2. 按一下工作表，將焦點移至設計工具。

3. 按一下 [功能區] 上的 [開發人員] **** 索引標籤。

    > [!NOTE]
    > 如果 [開發人員] **** 索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [ **XML** ] 群組中，按一下 [**來源**]。

     [ **XML 來源**] 視窗隨即開啟。

5. 在 [ **Xml 來源**] 視窗中，按一下 [ **xml 對應**]。

     [ **XML 對應**] 對話方塊隨即開啟。

6. 在 [ **XML 對應**] 對話方塊中，按一下 [**加入**]。

7. 流覽至您的架構檔案，加以選取，然後按一下 [**開啟**]。

8. 按一下 [確定] 。

     架構會在 [ **XML 來源**] 視窗中表示。 在您的專案中， <xref:System.Data.DataSet> 會根據架構產生具型別，並 <xref:System.Windows.Forms.BindingSource> 建立。

9. 將專案從 [ **XML 來源**] 視窗拖曳至您要在其中建立對應控制項的工作表位置。

     如果您拖曳非重複的架構元素，Office 專案會產生自動系結 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 至的控制項 <xref:System.Windows.Forms.BindingSource> 。

     如果您拖曳重複的架構元素，Office 專案 <xref:Microsoft.Office.Tools.Excel.ListObject> 會產生不會自動系結至資料來源的控制項。 如需詳細資訊，請參閱[檔層級自訂中的 XML 架構和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。

## <a name="see-also"></a>另請參閱
- [如何：在 Visual Studio 內將架構對應至 Word 檔](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [檔層級自訂中的 XML 架構和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
