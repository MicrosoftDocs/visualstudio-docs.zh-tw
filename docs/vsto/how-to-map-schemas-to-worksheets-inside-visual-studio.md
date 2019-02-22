---
title: HOW TO：將結構描述對應至 Visual Studio 內的工作表
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0fad2851be48c0b3dfc3546794d5b9907f55918a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637369"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>HOW TO：將結構描述對應至 Visual Studio 內的工作表
  Visual Studio 中開啟工作表時，您可以將 XML 結構描述對應至工作表中。 您使用 Visual Studio 外部開啟活頁簿時，您所使用的相同 Microsoft Office Excel 工具。 是否將結構描述對應至工作表之前，或建立您的 Excel 解決方案之後，Office 專案就會建立相同的物件。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
>  您無法在 Excel 方案中使用多部分的 XML 結構描述。

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>若要將 XML 結構描述對應至 Visual Studio 中的 Excel 工作表

1.  開啟 Visual Studio 內的 Excel 活頁簿或範本專案。

2.  按一下要將焦點移至設計工具的工作表中。

3.  按一下 [功能區] 上的 [開發人員]  索引標籤。

    > [!NOTE]
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。

4.  在  **XML**群組中，按一下**來源**。

     **XML 來源**視窗隨即開啟。

5.  在 [ **XML 來源**] 視窗中，按一下**XML 對應**。

     **XML 對應**對話方塊隨即開啟。

6.  在 [ **XML 對應**] 對話方塊中，按一下**新增**。

7.  瀏覽至您的結構描述檔案，加以選取，然後按一下 **開啟**。

8.  按一下 [確定] 。

     結構描述會以表示**XML 來源**視窗。 在專案中，具型別<xref:System.Data.DataSet>會根據結構描述，產生和<xref:System.Windows.Forms.BindingSource>建立。

9. 將項目從拖曳**XML 來源**視窗的位置，工作表中您想要建立對應的控制項。

     如果您拖曳的非重複的結構描述項目時，Office 專案會產生<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>自動繫結至控制項<xref:System.Windows.Forms.BindingSource>。

     如果您將重複的結構描述項目時，Office 專案會產生<xref:Microsoft.Office.Tools.Excel.ListObject>未自動繫結至資料來源的控制項。 如需詳細資訊，請參閱 < [XML 結構描述和資料在文件層級自訂](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。

## <a name="see-also"></a>另請參閱
- [如何：將結構描述對應至 Visual Studio 中的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML 結構描述和文件層級自訂中的資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
