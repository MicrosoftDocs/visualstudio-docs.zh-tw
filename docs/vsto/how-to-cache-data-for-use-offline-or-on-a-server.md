---
title: 如何：快取資料供離線使用或在伺服器上使用
description: 標記要在檔中快取的資料項目，使其可供離線使用。 這讓檔中的資料可以由其他程式碼操作。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ab53676d6c00fdda3bb7f4554321f0c0550e5748
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954042"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>如何：快取資料供離線使用或在伺服器上使用
  您可以標示要在檔中快取的資料項目，使其可供離線使用。 這也可讓檔中的資料在儲存在伺服器上時，由其他程式碼操作。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 您可以在程式碼中宣告資料項目時，標示要快取的資料項目，如果您是使用，則可以在 <xref:System.Data.DataSet> [ **屬性** ] 視窗中設定屬性，來標示要快取的資料項目。 如果您要快取非或的資料項目 <xref:System.Data.DataSet> <xref:System.Data.DataTable> ，請確定它符合在檔中快取的準則。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

> [!NOTE]
> 使用標記為快 **取和** **WithEvents** 的 Visual Basic 所建立的資料集 (包括從 [**資料來源**] 視窗或 [ **CacheInDocument** ] 屬性設定為 **True** 的 [**工具箱**] 中拖曳的資料集) 在快取中的名稱前面會加上底線。 例如，如果您建立資料集，並將它命名為 **Customers**，則 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 會在快取中 **_Customers** 名稱。 當您使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 來存取這個快取的專案時，您必須指定 **_Customers** 而不是 **客戶**。

### <a name="to-cache-data-in-the-document-using-code"></a>使用程式碼快取檔中的資料

1. 將資料項目的公用欄位或屬性宣告為專案中主專案類別的成員，例如 `ThisDocumen` Word 專案中的 t 類別或 `ThisWorkbook` Excel 專案中的類別。

2. 將屬性套用至 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 成員，以將資料項目標記為儲存在檔的資料快取中。 下列範例會將這個屬性套用至的欄位宣告 <xref:System.Data.DataSet> 。

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. 加入程式碼以建立資料項目的實例（如果適用的話），以從資料庫載入該專案。

     資料項目目只會在第一次建立時載入;之後，快取會保留在檔中，而您必須撰寫其他程式碼來更新它。

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>若要使用屬性視窗快取檔中的資料集

1. 使用 Visual Studio 設計工具中的工具，將資料集加入至專案，例如，使用 [ **資料來源** ] 視窗，將資料來源新增至您的專案。

2. 如果您還沒有資料集的實例，請建立一個實例，然後在設計工具中選取該實例。

3. 在 [ **屬性** ] 視窗中，將 [ **CacheInDocument** ] 屬性設定為 [ **True**]。

     如需詳細資訊，請參閱 [Office 專案中的屬性](../vsto/properties-in-office-projects.md)。

4. 在 [ **屬性** ] 視窗中， **將 [修飾** 詞] 屬性設定為 [ **Public** (預設為 **內部**) 。

## <a name="see-also"></a>另請參閱
- [快取資料](../vsto/caching-data.md)
- [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [儲存資料](../data-tools/save-data-back-to-the-database.md)
