---
title: "如何： 對應至 Visual Studio 內的工作表的結構描述 |Microsoft 文件"
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2dc089fb2c4ae2714a0b94d7756aaa432406ef74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>如何：在 Visual Studio 內將結構描述對應至工作表
  Visual Studio 中開啟工作表時，您可以將 XML 結構描述對應至工作表中。 您使用相同的 Microsoft Office Excel 工具，您可以使用 Visual Studio 外部開啟活頁簿時。 將結構描述對應至工作表之前或之後建立 Excel 方案的 Office 專案會建立相同的物件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  您無法在 Excel 方案中使用多部分的 XML 結構描述。  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>若要將 XML 結構描述對應至 Visual Studio 中的 Excel 工作表  
  
1.  開啟 Visual Studio 內的 Excel 活頁簿或範本專案。  
  
2.  按一下要將焦點移至設計工具的工作表中。  
  
3.  按一下 [功能區] 上的 [開發人員]  索引標籤。  
  
    > [!NOTE]  
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  在**XML**群組中，按一下**來源**。  
  
     **XML 來源**視窗隨即開啟。  
  
5.  在**XML 來源**視窗中，按一下  **XML 對應**。  
  
     **XML 對應**對話方塊隨即開啟。  
  
6.  在**XML 對應**對話方塊中，按一下 **新增**。  
  
7.  瀏覽至您的結構描述檔案，加以選取，然後按**開啟**。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
     結構描述中表示**XML 來源**視窗。 在專案中，具型別的<xref:System.Data.DataSet>會根據結構描述，產生和<xref:System.Windows.Forms.BindingSource>建立。  
  
9. 拖曳項目從**XML 來源**到您想要建立對應的控制項的位置工作表中的視窗。  
  
     如果您拖曳的非重複結構描述項目時，Office 專案會產生<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>自動繫結至控制項<xref:System.Windows.Forms.BindingSource>。  
  
     如果您將重複的結構描述項目時，Office 專案會產生<xref:Microsoft.Office.Tools.Excel.ListObject>不會自動繫結至資料來源的控制項。 如需詳細資訊，請參閱[XML 結構描述和文件層級自訂中的資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 將結構描述對應至 Visual Studio 內的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [文件層級自訂中的 XML 結構描述和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  