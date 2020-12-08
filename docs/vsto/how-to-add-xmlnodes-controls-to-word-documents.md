---
title: 如何：將 XMLNodes 控制項加入至 Word 檔
description: 瞭解當您將重複的 XML 架構元素對應到 Microsoft Office Word 檔時，Visual Studio 會自動將 XMLNodes 控制項新增至您的檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 256c62fc69be2c057d3ffc2588577fa87910c161
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844435"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>如何：將 XMLNodes 控制項加入至 Word 檔
  **重要** 本主題中有關 Microsoft Word 的資訊，只會提供給位於美國以外的個人和組織，或使用或正在開發的 microsoft word 產品（在2010年1月之前由 Microsoft 授權的 microsoft Word 產品），而 Microsoft 已從 Microsoft Word 移除與自訂 XML 相關的特定功能。 這項有關 Microsoft Word 的資訊，可能無法由美國的個人或組織、在2010年1月10日之後由 Microsoft 授權的 Microsoft Word 產品所使用的 microsoft word 產品或開發人員所使用;這些產品的行為不像在該日期之前授權的產品，或購買並授權在美國以外地區使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 當您將重複的 XML 架構元素對應到 Microsoft Office Word 檔時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項加入檔。

 如需對應非重複 XML 架構元素的詳細資訊，請參閱 [如何：將 XMLNode 控制項新增至 Word 檔](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNodes>控制項無法從 [**工具箱**] 或 [**資料來源**] 視窗使用，也無法以程式設計方式建立。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>將 XMLNodes 控制項加入至檔

1. 在 Visual Studio 設計工具的檔中，按一下功能區上的 [ **開發人員** ] 索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

2. 在 [ **XML** ] 群組中，按一下 [ **架構**]。

     [ **範本和增益集** ] 對話方塊隨即開啟。

3. 按一下 [ **XML 架構** ] 索引標籤。

4. 按一下 [ **新增架構**]。

     [ **新增架構** ] 對話方塊隨即開啟。

5. 選取包含重複架構元素的 XML 架構，然後按一下 [ **開啟**]。

     [ **架構設定** ] 對話方塊隨即出現。

6. 指派別名或按一下 **[確定]** ，以新增沒有別名的架構。

     架構就會加入至 [ **加入架構** ] 對話方塊中。

7. 在 [ **新增架構** ] 對話方塊中，按一下 **[確定]**。

     [ **XML 結構** ] 工作窗格隨即開啟。

8. 按一下 [ **XML 結構** ] 工作窗格上的 [重複架構] 元素，將它加入至檔。

     <xref:Microsoft.Office.Tools.Word.XMLNodes>系統會建立控制項，並將其加入至專案。

## <a name="see-also"></a>另請參閱
- [XMLNodes 控制項](../vsto/xmlnodes-control.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
