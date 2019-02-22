---
title: HOW TO：離線或在伺服器上快取資料以供使用
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bae12ea054c674e14da53fe60879c5466120d0a9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636511"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>HOW TO：離線或在伺服器上快取資料以供使用
  您可以將標記資料項目，以快取中的文件，如此就可以使用離線。 這也使得資料可能儲存在伺服器的文件，會由其他程式碼操作文件中。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以將標記或快取您的程式碼中宣告的資料項目時，如果您使用的資料項目<xref:System.Data.DataSet>，設定屬性**屬性**視窗。 如果您要快取不資料項目<xref:System.Data.DataSet>或<xref:System.Data.DataTable>，確保其符合所快取文件中的準則。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。

> [!NOTE]
>  使用標示為 Visual Basic 建立的資料集**快取**並**WithEvents** (包括從拖曳的資料集**Zdroje dat**視窗或**工具箱**具有**CacheInDocument**屬性設定為 **，則為 True**) 已在快取其名稱前面加上底線。 例如，如果您建立資料集並將它命名**客戶**，則<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>名稱會是 **_Customers**快取中。 當您使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>若要存取此快取的項目，您必須指定 **_Customers**而非**客戶**。

### <a name="to-cache-data-in-the-document-using-code"></a>使用程式碼文件中的快取資料

1.  例如在您專案中，主項目類別的成員身分宣告公用欄位或屬性資料項目`ThisDocumen`Word 專案中的 t 類別或`ThisWorkbook`Excel 專案中的類別。

2.  套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性儲存在文件的資料快取的資料項目標記的成員。 下列範例將此屬性套用至欄位宣告<xref:System.Data.DataSet>。

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  加入程式碼來建立資料的項目執行個體，如果適用，可從資料庫中載入。

     第一次建立時，只載入資料的項目因此，快取會跟著文件，您必須撰寫其他程式碼以更新它。

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>若要使用 [屬性] 視窗，快取文件中的資料集

1.  加入專案中的資料集，使用 Visual Studio 設計工具中，比方說，藉由將您的專案使用的資料來源**Zdroje dat**視窗。

2.  如果您還沒沒有帳戶，並在設計工具中選取的執行個體，請建立資料集執行個體。

3.  在 **屬性**視窗中，將**CacheInDocument**屬性設**True**。

     如需詳細資訊，請參閱 < [Properties in Office Projects](../vsto/properties-in-office-projects.md)。

4.  在 **屬性**視窗中，將**修飾詞**屬性設**公用**(根據預設，它是**內部**)。

## <a name="see-also"></a>另請參閱
- [快取資料](../vsto/caching-data.md)
- [如何：以程式設計方式快取 Office 文件中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [如何：在受密碼保護的文件中的快取資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [將資料儲存](../data-tools/saving-data.md)
