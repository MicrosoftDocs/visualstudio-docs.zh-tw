---
title: "如何： 將結構描述對應至 Visual Studio 內的 Word 文件 |Microsoft 文件"
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
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c185e44cb01fd1908a477f5e9b7ef096472f4b00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>如何：在 Visual Studio 內將結構描述對應至 Word 文件
  **重要**本主題有關 Microsoft Word 中設定的資訊是呈現專用的效益和使用個人和組織使用者位於美國和其領域之外或人員使用，或開發在執行的程式，已由 Microsoft 授權年 1 月 2010、 Microsoft 實作的特定功能中移除時之前的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 不能讀取或由個人或組織在美國或其領域人員使用，或是在開發已由 Microsoft 授權，2010 年 1 月 10 日之後的 Microsoft Word 產品執行的程式中使用這項資訊有關 Microsoft Word;這些產品無法運作此日期之前的授權或購買與授權在美國以外的產品相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Visual Studio 中開啟文件時，您可以將 XML 結構描述對應至文件中。 您使用 Visual Studio 外部開啟文件時，您使用的相同 Microsoft Office Word 工具。 將結構描述對應至文件之前或之後建立 Word 方案的 Office 專案會建立相同的物件。  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>若要將 XML 結構描述對應至 Visual Studio 中的 Word 文件  
  
1.  開啟 Visual Studio 內的 Word 文件或範本專案。  
  
2.  按一下要將焦點移至設計工具的文件中。  
  
3.  按一下 [功能區] 上的 [開發人員]  索引標籤。  
  
    > [!NOTE]  
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  在**XML**群組中，按一下**結構描述**。  
  
     **範本與增益集**對話方塊隨即開啟。  
  
5.  按一下**XML 結構描述** 索引標籤。  
  
6.  按一下**新增結構描述**。  
  
     **新增結構描述**對話方塊隨即開啟。  
  
7.  瀏覽至您的結構描述檔案，加以選取，然後按**開啟**。  
  
     **結構描述設定**對話方塊隨即開啟。  
  
8.  指派別名，或按一下**確定**加入不含別名的結構描述。  
  
9. 按一下 [確定 **Deploying Office Solutions**]。  
  
     **XML 結構**視窗隨即開啟。  
  
10. 拖曳項目從**XML 結構**視窗到文件中您想要建立對應的控制項的位置。  
  
## <a name="see-also"></a>請參閱  
 [如何： 將結構描述對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [文件層級自訂中的 XML 結構描述和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  