---
title: 如何：將 XMLNode 控制項新增至 Word 檔
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: bd0429374b175da3260c3605f39c90cf2dffb841
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544894"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>如何：將 XMLNode 控制項新增至 Word 檔
  **重要事項**本主題中針對 Microsoft Word 所設定的資訊，僅適用于在美國境內和其區域以外的個人和組織，或是在 microsoft 從 microsoft Word 移除與自訂 XML 相關的特定功能時，在2010年1月之前，由 Microsoft 授權的 Microsoft Word 產品的權益與使用方式。 這項關於 Microsoft Word 的資訊，可能無法由美國或其所在地區的個人或組織，或其使用或開發在 Microsoft Word 產品于2010年1月10日之後授權的 Microsoft 文字軟體所閱讀或使用。這些產品的行為不會與在該日期之前授權的產品相同，或購買並授權在美國以外使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 當您將非重複的 XML 架構專案對應到 Microsoft Office Word 檔時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項加入至您的檔。 如需對應重複 XML 架構元素的詳細資訊，請參閱[如何：將 XMLNodes 控制項新增至 Word 檔](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)。

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNode>控制項無法從 [**工具箱**] 或 [**資料來源**] 視窗使用，而且無法以程式設計方式建立。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>將 XMLNode 控制項新增至檔

1. 在 Visual Studio 設計工具的檔中，按一下功能區上的 [**開發人員**] 索引標籤。

    > [!NOTE]
    > 如果 [開發人員] **** 索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

2. 在 [ **XML** ] 群組中，按一下 [**架構**]。

     [**範本與增益集**] 對話方塊隨即開啟。

3. 按一下 [ **XML 架構**] 索引標籤。

4. 按一下 [**新增架構**]。

     [**加入架構**] 對話方塊隨即開啟。

5. 從 [**加入架構**] 對話方塊中，選取包含非重複架構元素的 XML 架構，然後按一下 [**開啟**]。

     [**架構設定**] 對話方塊隨即出現。

6. 指派別名，或按一下 **[確定]** 以新增不含別名的架構。

     架構就會加入至 [**加入架構**] 對話方塊。

7. 在 [**新增架構**] 對話方塊中，按一下 **[確定]**。

8. [ **XML 結構**] 工作窗格隨即開啟。

9. 按一下 [ **XML 結構**] 工作窗格上的 [非重複的架構] 專案，將它加入檔中。

     <xref:Microsoft.Office.Tools.Word.XMLNode>隨即會建立控制項並將其加入至專案。

## <a name="see-also"></a>另請參閱
- [XMLNode 控制項](../vsto/xmlnode-control.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
