---
title: 如何：在 Visual Studio 內將架構對應至 Word 檔
titleSuffix: ''
ms.custom: seodec18
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
ms.openlocfilehash: 281d9dc18ae1d0550ba844e58d4e39c3723c8dfb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538147"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>如何：在 Visual Studio 內將架構對應至 Word 檔
  **重要事項**本主題中針對 Microsoft Word 所設定的資訊，僅適用于在美國境內和其區域以外的個人和組織，或是在 microsoft 從 microsoft Word 移除與自訂 XML 相關的特定功能時，在2010年1月之前，由 Microsoft 授權的 Microsoft Word 產品的權益與使用方式。 這項關於 Microsoft Word 的資訊，可能無法由美國或其所在地區的個人或組織，或其使用或開發在 Microsoft Word 產品于2010年1月10日之後授權的 Microsoft 文字軟體所閱讀或使用。這些產品的行為不會與在該日期之前授權的產品相同，或購買並授權在美國以外使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 在 Visual Studio 中開啟檔時，您可以將 XML 架構對應至檔。 當檔在 Visual Studio 外開啟時，您會使用相同的 Microsoft Office Word 工具。 無論您是在建立 Word 方案之前或之後，將架構對應至檔，Office 專案都會建立相同的物件。

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>若要將 XML 架構對應至 Word 檔，請 Visual Studio

1. 在 Visual Studio 內開啟 Word 檔或範本專案。

2. 按一下檔，將焦點移至設計工具。

3. 在功能區上，按一下 [**開發人員**] 索引標籤。

    > [!NOTE]
    > 如果 [開發人員] **** 索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

4. 在 [ **XML** ] 群組中，按一下 [**架構**]。

     [**範本與增益集**] 對話方塊隨即開啟。

5. 按一下 [ **XML 架構**] 索引標籤。

6. 按一下 [**新增架構**]。

     [**加入架構**] 對話方塊隨即開啟。

7. 流覽至您的架構檔案，加以選取，然後按一下 [**開啟**]。

     [**架構設定**] 對話方塊隨即開啟。

8. 指派別名，或按一下 **[確定]** 以新增不含別名的架構。

9. 按一下 [確定] 。

     [ **XML 結構**] 視窗隨即開啟。

10. 將專案從 [ **XML 結構**] 視窗拖曳至您想要建立對應控制項之檔中的位置。

## <a name="see-also"></a>另請參閱
- [如何：將架構對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [檔層級自訂中的 XML 架構和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
