---
title: "如何： 將 XMLNode 控制項加入 Word 文件 |Microsoft 文件"
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
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a24f5b4205a558e950a7fe941ac6f8a3e7c45068
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>如何：將 XMLNode 控制項加入至 Word 文件
  **重要**本主題有關 Microsoft Word 中設定的資訊是呈現專用的效益和使用個人和組織使用者位於美國和其領域之外或人員使用，或開發在執行的程式，已由 Microsoft 授權年 1 月 2010、 Microsoft 實作的特定功能中移除時之前的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 不能讀取或由個人或組織在美國或其領域人員使用，或是在開發已由 Microsoft 授權，2010 年 1 月 10 日之後的 Microsoft Word 產品執行的程式中使用這項資訊有關 Microsoft Word;這些產品無法運作此日期之前的授權或購買與授權在美國以外的產品相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 當您在非重複的 XML 結構描述元素對應到 Microsoft Office Word 文件時，Visual Studio 會自動加入<xref:Microsoft.Office.Tools.Word.XMLNode>控制項加入文件。 重複的 XML 結構描述項目對應的相關資訊，請參閱[How to： 將 XMLNodes 控制項加入 Word 文件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode>控制項不是可從**工具箱**或**資料來源**視窗中，而且不能以程式設計方式建立。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>XMLNode 控制項加入文件  
  
1.  在 Visual Studio 設計工具中，在功能區 中的文件中按一下**開發人員** 索引標籤。  
  
    > [!NOTE]  
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
2.  在**XML**群組中，按一下**結構描述**。  
  
     **範本與增益集**對話方塊隨即開啟。  
  
3.  按一下**XML 結構描述** 索引標籤。  
  
4.  按一下**新增結構描述**。  
  
     **新增結構描述**對話方塊隨即開啟。  
  
5.  選取包含非重複的結構描述元素的 XML 結構描述**新增結構描述**對話方塊，按一下**開啟**。  
  
     **結構描述設定** 對話方塊隨即出現。  
  
6.  指派別名，或按一下**確定**加入不含別名的結構描述。  
  
     結構描述加入至**新增結構描述** 對話方塊。  
  
7.  在**新增結構描述**對話方塊中，按一下 **確定**。  
  
8.  **XML 結構**工作窗格隨即開啟。  
  
9. 按一下非重複結構描述項目**XML 結構**工作窗格，以將它加入至文件。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode>控制已建立並加入至專案。  
  
## <a name="see-also"></a>另請參閱  
 [XMLNode 控制項](../vsto/xmlnode-control.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  