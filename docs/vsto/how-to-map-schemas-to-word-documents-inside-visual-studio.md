---
title: 如何：將架構對應至 Visual Studio 內的 Word 檔
description: 瞭解如何在 Visual Studio 中開啟檔時，將 XML 架構對應至 Microsoft Office Word 檔。
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 427e2fcb9b881305c160b906262f251d32d70981
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848218"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>如何：將架構對應至 Visual Studio 內的 Word 檔
  **重要** 本主題中有關 Microsoft Word 的資訊，只會提供給位於美國以外的個人和組織，或使用或正在開發的 microsoft word 產品（在2010年1月之前由 Microsoft 授權的 microsoft Word 產品），而 Microsoft 已從 Microsoft Word 移除與自訂 XML 相關的特定功能。 這項有關 Microsoft Word 的資訊，可能無法由美國的個人或組織、在2010年1月10日之後由 Microsoft 授權的 Microsoft Word 產品所使用的 microsoft word 產品或開發人員所使用;這些產品的行為不像在該日期之前授權的產品，或購買並授權在美國以外地區使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 在 Visual Studio 中開啟檔時，您可以將 XML 架構對應至檔。 當檔在 Visual Studio 外部開啟時，您會使用相同的 Microsoft Office Word 工具。 無論您是在建立 Word 方案之前或之後將架構對應至檔，Office 專案都會建立相同的物件。

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>若要將 XML 架構對應至 Visual Studio 中的 Word 檔

1. 開啟 Visual Studio 內的 Word 檔或範本專案。

2. 按一下檔以將焦點移至設計工具。

3. 在功能區中，按一下 [ **開發人員** ] 索引標籤。

    > [!NOTE]
    > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [ **XML** ] 群組中，按一下 [ **架構**]。

     [ **範本和增益集** ] 對話方塊隨即開啟。

5. 按一下 [ **XML 架構** ] 索引標籤。

6. 按一下 [ **新增架構**]。

     [ **新增架構** ] 對話方塊隨即開啟。

7. 流覽至您的架構檔案，選取它，然後按一下 [ **開啟**]。

     [ **架構設定** ] 對話方塊隨即開啟。

8. 指派別名或按一下 **[確定]** ，以新增沒有別名的架構。

9. 按一下 [確定]。

     [ **XML 結構** ] 視窗隨即開啟。

10. 將專案從 [ **XML 結構** ] 視窗拖曳到您的檔中要建立對應控制項的位置。

## <a name="see-also"></a>另請參閱
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [檔層級自訂中的 XML 架構和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
