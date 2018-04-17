---
title: 快取資料 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>快取資料
  您可以快取文件層級自訂中的資料物件，以便可存取資料，而不需要開啟 Microsoft Office Word 或 Microsoft Office Excel 或離線。 若要快取物件，該物件必須符合特定需求的資料類型。 .NET Framework 中的許多常見的資料類型符合這些需求，包括<xref:System.String>， <xref:System.Data.DataSet>，和<xref:System.Data.DataTable>。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有兩種方式可將物件加入至資料快取：  
  
-   若要建置方案時，請將物件加入至資料快取中，套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>物件宣告此屬性。 如需詳細資訊，請參閱[How to： 使用離線或在伺服器上的快取資料](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   若要以程式設計方式加入的資料快取執行階段物件，使用`StartCaching`方法的主機項目，例如`ThisDocument`或`ThisWorkbook`類別。 如需詳細資訊，請參閱[How to： 以程式設計方式快取 Office 文件中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
 您將物件加入至資料快取之後，您可以存取和修改快取的資料，而不啟動 Word 或 Excel。 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>快取的資料物件的需求  
 若要快取方案中的資料物件，該物件必須符合下列需求：  
  
-   是讀取/寫入公用欄位或屬性的主項目，例如`ThisDocument`或`ThisWorkbook`類別。  
  
-   不是索引子或其他參數化的屬性。  
  
 此外，資料物件必須可由<xref:System.Xml.Serialization.XmlSerializer>類別，這表示的物件型別必須具有下列特性：  
  
-   是公用型別。  
  
-   有不含任何參數的公用建構函式。  
  
-   不會執行需要額外的安全性權限的程式碼。  
  
-   公開只讀取/寫入的公用屬性 （會忽略其他屬性）。  
  
-   不會公開 （接受巢狀的陣列） 的多維陣列。  
  
-   從屬性和欄位傳回的介面。  
  
-   未實作<xref:System.Collections.IDictionary>如果的集合。  
  
 當您快取資料物件，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]將物件序列化成 XML 字串儲存在*自訂 XML 組件*文件中。 如需詳細資訊，請參閱 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)。  
  
## <a name="cached-data-size-limits"></a>快取的資料大小限制  
 有一些限制，您可以加入在文件中的資料快取和資料快取中的任何個別物件的大小的資料總量。 如果您超過這些限制時，應用程式可能會在儲存資料的資料快取時非預期地關閉。  
  
 若要避免這些限制，請遵循這些指導方針：  
  
-   請勿將大於 10 MB 的任何物件的資料快取。  
  
-   請勿將單一文件中的資料快取中多個 100 MB 的總資料。  
  
 這些是大約值。 確切的限制，取決於許多因素，包括可用的 RAM 和執行的處理程序的數目。  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>控制快取物件的行為  
 若要更充分掌控快取物件的行為，您可以實作<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>介面上的快取的物件類型。 例如，您可以實作這個介面，如果您想要控制已變更物件時，如何通知使用者。 對於程式碼範例示範如何實作<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>，請參閱`ControlCollection`類別中的動態控制項範例 Excel 和 Word 動態控制項範例中[Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>快取的資料在受密碼保護的文件中保存變更  
 如果您要快取受密碼保護的文件中的資料物件，不會儲存快取的資料變更。 您可以透過兩種方法的覆寫快取的資料儲存變更。 覆寫這些方法來暫時儲存文件時，請移除保護，然後重新套用的保護，在儲存作業已完成。  
  
 如需詳細資訊，請參閱[How to： 遺失了資料文件中的快取資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>將 Null 值加入至資料快取時防止資料遺失  
 當您將物件加入資料快取時，所有快取的物件必須初始化為非**null**值之前儲存和關閉文件。 如果任何快取的物件具有**null**值儲存和關閉文件時[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]將自動移除所有的快取物件從資料快取。  
  
 如果您加入的物件**null**值使用的資料快取<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性在設計階段，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，以初始化快取的資料物件，才能在開啟文件。 這非常有用，如果您想要初始化沒有 Word 或 Excel 之前, 安裝在終端使用者開啟文件的伺服器上的快取的資料。 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 使用快取資料，離線或伺服器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何： 以程式設計方式快取中的 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何： 快取受密碼保護的文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [逐步解說：使用快取資料集來建立主從式關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  