---
title: 快取資料
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
ms.openlocfilehash: 2d106209accb5c67d6b9ab24a15aa7edd79d11be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846885"
---
# <a name="cache-data"></a>快取資料
  您可以快取文件層級自訂中的資料物件，所以離線狀態或無需開啟 Microsoft Office Word 或 Microsoft Office Excel，就可以存取的資料。 若要快取物件，該物件必須符合特定需求的資料類型。 許多常見的資料型別，.NET Framework 中符合這些需求，包括<xref:System.String>， <xref:System.Data.DataSet>，和<xref:System.Data.DataTable>。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有兩種方式可將物件加入至資料快取：  
  
- 若要建置方案時，請將物件加入至資料快取中，將套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性加入物件常值。 如需詳細資訊，請參閱 <<c0> [ 如何： 快取資料以供使用，離線或在伺服器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
- 若要以程式設計方式加入物件的資料快取在執行階段，請使用`StartCaching`方法的許多項目，例如`ThisDocument`或`ThisWorkbook`類別。 如需詳細資訊，請參閱 <<c0> [ 如何： 以程式設計方式快取 Office 文件中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
  您將物件加入至資料快取之後，您可以存取和修改快取的資料，而不啟動 Word 或 Excel。 如需詳細資訊，請參閱 <<c0> [ 存取在伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>快取的資料物件的需求  
 若要快取您的方案中的資料物件，該物件必須符合下列需求：  
  
- 是讀取/寫入公用欄位或屬性的主項目，例如`ThisDocument`或`ThisWorkbook`類別。  
  
- 不是索引子或其他的參數化的屬性。  
  
  此外，資料物件必須由序列化<xref:System.Xml.Serialization.XmlSerializer>類別，這表示物件的類型必須具有下列特性：  
  
- 是公用型別。  
  
- 有任何參數的公用建構函式。  
  
- 執行需要額外的安全性權限的程式碼。  
  
- 公開只讀取/寫入的公用屬性 （其他屬性都會被忽略）。  
  
- 不會公開 （接受巢狀的陣列） 的多維陣列。  
  
- 不會從屬性和欄位傳回的介面。  
  
- 未實作<xref:System.Collections.IDictionary>如果集合。  
  
  當您快取資料物件[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]將物件序列化成 XML 字串儲存在*自訂 XML 組件*文件中。 如需詳細資訊，請參閱 <<c0> [ 自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
## <a name="cached-data-size-limits"></a>快取的資料大小限制  
 有一些限制，您可以新增在文件中的資料快取和大小的資料快取中的任何個別物件的資料總量。 如果您超過這些限制，應用程式可能會在資料儲存至資料快取時非預期地關閉。  
  
 若要避免這些限制，請遵循這些指導方針：  
  
- 請勿將大於 10 MB 的任何物件加入的資料快取。  
  
- 請勿將多個 100 MB 的資料總計加入單一文件中的資料快取。  
  
  這些是近似的值。 確切的限制取決於許多因素，包括可用的 RAM 和執行程序的數目。  
  
## <a name="control-the-behavior-of-cached-objects"></a>控制快取物件的行為  
 若要進一步控制快取物件的行為，您可以實作<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>介面上的快取的物件類型。 例如，您可以實作這個介面，如果您想要控制已變更物件時，如何通知使用者。 如需程式碼範例示範如何實作<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>，請參閱 <<c2> `ControlCollection` 中的動態控制項範例 Excel 和 Word 動態控制項範例中的類別[Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>保存在受密碼保護的文件中的快取資料的變更  
 如果您要快取受密碼保護的文件中的資料物件，不會儲存快取的資料變更。 您可以藉由覆寫兩種方法，來快取的資料儲存變更。 覆寫這些方法來儲存文件時，暫時移除保護，然後重新套用儲存後的保護作業已完成。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 快取受密碼保護的文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>加入的資料快取中的 null 值時，避免資料遺失  
 當您將物件加入的資料快取時，所有快取的物件必須初始化為非**null**值之前儲存和關閉文件。 如果任何快取的物件具有**null**值儲存和關閉文件時[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]會自動移除快取物件的所有資料快取中。  
  
 如果您加入的物件**null**值使用的資料快取<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性在設計階段，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別，以初始化快取的資料物件，然後在開啟文件才。 這非常有用，如果您想要初始化不含 Word 或 Excel 之前由使用者開啟文件安裝在伺服器上快取的資料。 如需詳細資訊，請參閱 <<c0> [ 存取在伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 快取資料以供使用，離線或在伺服器上](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何： 以程式設計方式快取 Office 文件中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何： 快取受密碼保護的文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [逐步解說： 建立使用快取的資料集的主版詳細資料關聯性](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  