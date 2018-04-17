---
title: 如何： 使用快取資料，離線或伺服器上 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91b50684e18aaf4b7b6d95d24c81ecb56bdefc4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>如何：快取資料供離線使用或於伺服器上使用
  您可以標示資料項目，快取中的文件，以便提供離線。 這也使得資料中操作其他程式碼時，文件儲存在伺服器上的文件。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以將標記或進行快取您的程式碼中宣告的資料項目時，如果您使用的資料項目<xref:System.Data.DataSet>，所設定的屬性**屬性**視窗。 如果您要快取資料項目不是<xref:System.Data.DataSet>或<xref:System.Data.DataTable>，確保其符合文件中所快取的準則。 如需詳細資訊，請參閱 [Caching Data](../vsto/caching-data.md)。  
  
> [!NOTE]  
>  使用標示為 Visual Basic 建立的資料集**快取**和**WithEvents** (包括資料集是指從拖曳**資料來源**視窗或**工具箱**具有**CacheInDocument**屬性設定為**True**) 具有其快取內的名稱前置底線。 例如，如果您建立資料集並將其命名**客戶**、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>名稱將會是**_Customers**快取中。 當您使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>若要存取此快取的項目，您必須指定**_Customers**而不是**客戶**。  
  
### <a name="to-cache-data-in-the-document-using-code"></a>使用程式碼文件中的快取資料  
  
1.  宣告的公用欄位或屬性資料的項目在專案中，主項目類別的成員身分像是`ThisDocumen`Word 專案中的 t 類別或`ThisWorkbook`Excel 專案中的類別。  
  
2.  套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性設定為要儲存文件的資料快取中的資料項目標記的成員。 下列範例將此屬性套用至欄位宣告為<xref:System.Data.DataSet>。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  加入程式碼來建立資料的項目執行個體和 （適用），若要從資料庫中載入。  
  
     初次建立; 時，就只載入資料的項目此後，快取保持與文件，而您必須撰寫其他程式碼以更新它。  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>若要使用 [屬性] 視窗，快取文件中的資料集  
  
1.  加入專案中的資料集，使用 Visual Studio 設計工具中，比方說，將資料來源加入至您的專案使用**資料來源**視窗。  
  
2.  如果您還未有一個，並在設計工具中選取的執行個體，請建立資料集的執行個體。  
  
3.  在**屬性**視窗中，將**CacheInDocument**屬性**True**。  
  
     如需詳細資訊，請參閱[Office 專案中的屬性](../vsto/properties-in-office-projects.md)。  
  
4.  在**屬性**視窗中，將**修飾詞**屬性**公用**(根據預設，它是**內部**)。  
  
## <a name="see-also"></a>另請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何： 以程式設計方式快取中的 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何： 快取受密碼保護的文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [在伺服器上的文件中存取資料](../vsto/accessing-data-in-documents-on-the-server.md)   
 [儲存資料](/visualstudio/data-tools/saving-data)  
  
  