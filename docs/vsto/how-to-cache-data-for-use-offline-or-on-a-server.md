---
title: 如何：快取資料以供離線使用或用於伺服器
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ce295e299e4accb2d79655675f6264a1497b8d69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546181"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>如何：快取資料以供離線使用或用於伺服器
  您可以標示要在檔中快取的資料項目，使其可在離線時使用。 這也可以讓檔中的資料在檔儲存于伺服器上時，由其他程式碼操作。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以在程式碼中宣告資料項目時，標記要快取的資料項目; 如果您正在使用 <xref:System.Data.DataSet> ，請在 [**屬性**] 視窗中設定屬性。 如果您要快取不是或的資料項目 <xref:System.Data.DataSet> <xref:System.Data.DataTable> ，請確定它符合檔中快取的準則。 如需詳細資訊，請參閱快取[資料](../vsto/caching-data.md)。

> [!NOTE]
> 使用標示為快**取和** **WithEvents**的 Visual Basic 所建立的資料集（包括從 [**資料來源**] 視窗或 [ **CacheInDocument** ] 屬性設定為**True**的**工具箱**拖曳的資料集）在快取中的名稱前面加上底線。 例如，如果您建立資料集並將其命名為**Customers**，此 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 名稱將會在快取中 **_Customers** 。 當您使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 來存取這個快取的專案時，您必須指定 **_Customers** ，而不是**客戶**。

### <a name="to-cache-data-in-the-document-using-code"></a>若要使用程式碼快取檔中的資料

1. 將資料項目的公用欄位或屬性宣告為專案中主專案類別的成員，例如 `ThisDocumen` Word 專案中的 t 類別或 `ThisWorkbook` Excel 專案中的類別。

2. 將 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性套用至成員，以標示要儲存在檔資料快取中的資料項目。 下列範例會將這個屬性套用至的欄位宣告 <xref:System.Data.DataSet> 。

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. 加入程式碼以建立資料項目的實例，如果適用的話，也可以從資料庫載入。

     只有在第一次建立資料項目目時，才會載入此資料項目;之後，快取會與檔保持一致，而且您必須撰寫其他程式碼來更新它。

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>若要使用屬性視窗快取檔中的資料集

1. 使用 Visual Studio 設計師中的工具，將資料集加入至專案，例如，使用 [**資料來源**] 視窗，將資料來源加入至專案。

2. 如果您還沒有資料集，請建立它的實例，然後在設計工具中選取實例。

3. 在 [**屬性**] 視窗中，將 [ **CacheInDocument** ] 屬性設定為 [ **True**]。

     如需詳細資訊，請參閱[Office 專案中的屬性](../vsto/properties-in-office-projects.md)。

4. 在 [**屬性**] 視窗中，將 [修飾詞 **] 屬性設為 [** **公用**] （預設為**內部**）。

## <a name="see-also"></a>另請參閱
- [快取資料](../vsto/caching-data.md)
- [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [存取伺服器上檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [儲存資料](../data-tools/save-data-back-to-the-database.md)
