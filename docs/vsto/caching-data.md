---
title: 快取資料
description: 瞭解如何在檔層級自訂中快取資料物件，讓資料可以離線存取，或不開啟 Microsoft Office Word 或 Excel。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f31556e64ee93a73fb09c27edd095bcd2653dfdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836159"
---
# <a name="cache-data"></a>快取資料
  您可以快取檔層級自訂中的資料物件，讓資料可以離線存取，或不開啟 Microsoft Office Word 或 Microsoft Office Excel。 若要快取物件，物件的資料類型必須符合特定需求。 .NET Framework 中的許多常見資料類型都符合這些需求，包括 <xref:System.String> 、 <xref:System.Data.DataSet> 和 <xref:System.Data.DataTable> 。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 有兩種方式可以將物件新增至資料快取：

- 若要在建立方案時將物件加入至資料快取，請將 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性套用至物件宣告。 如需詳細資訊，請參閱 [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

- 若要以程式設計方式在執行時間將物件加入至資料快取，請使用 `StartCaching` 主專案的方法，例如 `ThisDocument` 或 `ThisWorkbook` 類別。 如需詳細資訊，請參閱 [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。

  將物件加入至資料快取之後，您就可以在不啟動 Word 或 Excel 的情況下，存取和修改快取的資料。 如需詳細資訊，請參閱 [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。

## <a name="requirements-for-data-objects-to-be-cached"></a>要快取之資料物件的需求
 若要在方案中快取資料物件，物件必須符合下列需求：

- 這是主專案的讀取/寫入公用欄位或屬性，例如 `ThisDocument` 或 `ThisWorkbook` 類別。

- 不是索引子或其他參數化屬性。

  此外，此資料物件必須可由 <xref:System.Xml.Serialization.XmlSerializer> 類別序列化，這表示物件的型別必須具有下列特性：

- 為公用類型。

- 擁有不含參數的公用函式。

- 不執行需要額外安全性許可權的程式碼。

- 只公開讀取/寫入公用屬性 (其他屬性將會被忽略) 。

- )  (的嵌套陣列都不會公開多維度陣列。

- 無法從屬性和欄位傳回介面。

- <xref:System.Collections.IDictionary>如果集合，則不會執行。

  當您快取資料物件時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將物件序列化為 XML 字串，該字串會儲存在檔的 *自訂 xml 元件* 中。 如需詳細資訊，請參閱 [自訂 XML 元件總覽](../vsto/custom-xml-parts-overview.md)。

## <a name="cached-data-size-limits"></a>快取的資料大小限制
 您可以新增至檔中的資料快取，以及資料快取中任何個別物件大小的資料總量有一些限制。 如果您超過這些限制，當資料儲存至資料快取時，應用程式可能會意外關閉。

 若要避免這些限制，請遵循下列指導方針：

- 請勿將大於 10 MB 的任何物件新增至資料快取。

- 請勿將超過 100 MB 的總數據新增至單一檔中的資料快取。

  這些是大約的值。 確切的限制取決於數個因素，包括可用的 RAM 和執行中進程的數目。

## <a name="control-the-behavior-of-cached-objects"></a>控制快取物件的行為
 若要更充分掌控快取物件的行為，您可以在快取 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 物件的類型上執行介面。 例如，如果您想要控制在物件變更時如何通知使用者，您可以執行這個介面。 如需示範如何執行的程式碼範例 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> ，請參閱 `ControlCollection` Office 程式 [開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中 Excel 動態控制項範例和 Word 動態控制項範例中的類別。

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>保存受密碼保護檔中快取資料的變更
 如果您在以密碼保護的檔中快取資料物件，則不會儲存快取資料的變更。 您可以藉由覆寫兩個方法來儲存快取資料的變更。 覆寫這些方法，以在儲存檔時暫時移除保護，然後在儲存作業完成後重新套用保護。

 如需詳細資訊，請參閱 [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)。

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>將 null 值新增至資料快取時防止資料遺失
 當您將物件加入至資料快取時，必須先將所有快取的物件初始化為非 **null** 值，然後才儲存並關閉檔。 當儲存並關閉檔時，如果有任何快取物件具有 **null** 值，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動從資料快取中移除所有快取的物件。

 如果您在設計階段使用屬性將具有 **null** 值的物件加入至資料快取 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> ，您可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別在開啟檔之前初始化快取的資料物件。 如果您想要在不安裝 Word 或 Excel 的伺服器上初始化快取的資料，在使用者開啟檔之前，這會很有用。 如需詳細資訊，請參閱 [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。

## <a name="see-also"></a>另請參閱
- [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [如何：以程式設計方式快取 Office 檔中的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [如何：快取受密碼保護檔中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [逐步解說：使用快取資料集建立主要詳細資料關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
