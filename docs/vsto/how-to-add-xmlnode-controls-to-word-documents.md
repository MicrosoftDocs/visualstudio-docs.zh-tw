---
title: HOW TO：將 XMLNode 控制項加入 Word 文件
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 08ab6ab47ff3c916b2818d9cceac1ee839939a42
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638474"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>HOW TO：將 XMLNode 控制項加入 Word 文件
  **重要**本主題有關 Microsoft Word 中設定的資訊是提供專門用於權益與使用個人和組織使用者位於外部皒玿璅其領域，或使用，或開發在執行的程式，第 2010 年 1 月 Microsoft 何時移除特定功能的實作之前由 Microsoft 所授權的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 有關 Microsoft Word 的這項資訊可能不會讀取或使用的個人或組織在美國或其區域使用，或開發在 2010 年 1 月 10 日之後由 Microsoft 所授權的 Microsoft Word 產品執行的程式;這些產品無法運作此日期之前的授權或購買，以在美國以外的使用授權的產品相同。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 當您將非重複的 XML 結構描述元素對應至 Microsoft Office Word 文件時，Visual Studio 會自動將<xref:Microsoft.Office.Tools.Word.XMLNode>控制項加入文件。 如需對應重複的 XML 結構描述元素的資訊，請參閱[How to:XMLNodes 控制項加入 Word 文件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)。

> [!NOTE]
>  <xref:Microsoft.Office.Tools.Word.XMLNode>控制項不是可從**工具箱**或**Zdroje dat**視窗中，而且不能以程式設計方式建立。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>XMLNode 控制項加入文件

1.  在 Visual Studio 設計工具中，功能區中的文件中按一下**開發人員** 索引標籤。

    > [!NOTE]
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。

2.  在  **XML**群組中，按一下**結構描述**。

     **範本與增益集**對話方塊隨即開啟。

3.  按一下 [ **XML 結構描述**] 索引標籤。

4.  按一下 **新增結構描述**。

     **新增結構描述**對話方塊隨即開啟。

5.  選取包含非重複的結構描述元素的 XML 結構描述**新增結構描述**對話方塊，按一下**開啟**。

     **結構描述設定** 對話方塊隨即出現。

6.  指派別名，或按一下**確定**新增不含別名的結構描述。

     結構描述加入至**新增結構描述** 對話方塊。

7.  在 [**新增結構描述**] 對話方塊中，按一下**確定**。

8.  **XML 結構**工作窗格隨即開啟。

9. 按一下非重複的結構描述項目**XML 結構**工作窗格，即可將它新增至文件。

     <xref:Microsoft.Office.Tools.Word.XMLNode>控制已建立並加入至專案。

## <a name="see-also"></a>另請參閱
- [XMLNode 控制項](../vsto/xmlnode-control.md)
- [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
