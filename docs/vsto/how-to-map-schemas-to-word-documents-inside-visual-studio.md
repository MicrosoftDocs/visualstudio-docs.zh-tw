---
title: HOW TO：將結構描述對應至 Visual Studio 中的 Word 文件
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 37cdbc07f5defe0c6f8d5613795d2a9c6142521f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644701"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>HOW TO：將結構描述對應至 Visual Studio 中的 Word 文件
  **重要**本主題有關 Microsoft Word 中設定的資訊是提供專門用於權益與使用個人和組織使用者位於外部皒玿璅其領域，或使用，或開發在執行的程式，第 2010 年 1 月 Microsoft 何時移除特定功能的實作之前由 Microsoft 所授權的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 有關 Microsoft Word 的這項資訊可能不會讀取或使用的個人或組織在美國或其區域使用，或開發在 2010 年 1 月 10 日之後由 Microsoft 所授權的 Microsoft Word 產品執行的程式;這些產品無法運作此日期之前的授權或購買，以在美國以外的使用授權的產品相同。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 在 Visual Studio 中開啟文件時，您可以將 XML 結構描述對應至文件中。 您使用 Visual Studio 外部開啟文件時，您使用的相同 Microsoft Office Word 工具。 將結構描述對應至文件之前或之後建立 Word 方案的 Office 專案會建立相同的物件。

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>若要將 XML 結構描述對應至 Visual Studio 中的 Word 文件

1.  開啟 Visual Studio 中的 Word 文件或範本專案。

2.  按一下此選項，將焦點移至設計工具文件中。

3.  在功能區中，按一下**開發人員** 索引標籤。

    > [!NOTE]
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。

4.  在  **XML**群組中，按一下**結構描述**。

     **範本與增益集**對話方塊隨即開啟。

5.  按一下 [ **XML 結構描述**] 索引標籤。

6.  按一下 **新增結構描述**。

     **新增結構描述**對話方塊隨即開啟。

7.  瀏覽至您的結構描述檔案，加以選取，然後按一下 **開啟**。

     **結構描述設定**對話方塊隨即開啟。

8.  指派別名，或按一下**確定**新增不含別名的結構描述。

9. 按一下 [確定] 。

     **XML 結構**視窗隨即開啟。

10. 拖曳項目從**XML 結構**視窗，以在您的文件中您想要建立對應的控制項的位置。

## <a name="see-also"></a>另請參閱
- [如何：將結構描述對應至 Visual Studio 內的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML 結構描述和文件層級自訂中的資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
