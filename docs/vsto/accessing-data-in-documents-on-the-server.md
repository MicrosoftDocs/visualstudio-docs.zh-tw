---
title: 存取伺服器檔中的資料
description: 瞭解如何在檔層級自訂中針對資料進行程式設計，而不需要使用 Microsoft Office Word 或 Microsoft Office Excel 的物件模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0df6aef3c83d66b84f569e85e953fde8a3f0e16c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826768"
---
# <a name="access-data-in-documents-on-the-server"></a>存取伺服器檔中的資料
  您可以針對檔層級自訂中的資料進行程式設計，而不需要使用 Microsoft Office Word 或 Microsoft Office Excel 的物件模型。 這表示您可以在未安裝 Word 或 Excel 的伺服器上，存取包含在檔中的資料。 例如，伺服器上的程式碼 (例如，在頁面中 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]) 可以自訂檔中的資料，並將自訂檔傳送給終端使用者。 當使用者開啟檔時，方案元件中的資料系結程式碼會將自訂資料系結至檔。 這是可能的，因為檔中的資料與使用者介面分開。 如需詳細資訊，請參閱 [檔層級自訂中](../vsto/cached-data-in-document-level-customizations.md)的快取資料。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>快取用於伺服器的資料
 若要快取檔中的資料物件，請在設計階段將它標示為 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性，或 `StartCaching` 在執行時間使用主專案的方法。 當您快取檔中的資料物件時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將物件序列化為儲存在檔中的 XML 字串。 物件必須符合特定需求，才能符合快取的資格。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

 伺服器端程式碼可以操控資料快取中的任何資料物件。 系結至快取資料實例的控制項會與使用者介面進行同步處理，如此一來，當檔在用戶端上開啟時，就會自動顯示對資料所做的任何伺服器端變更。

## <a name="access-data-in-the-cache"></a>存取快取中的資料
 您可以從 Office 外部的應用程式（例如，從主控台應用程式、Windows Forms 應用程式或網頁）存取快取中的資料。 存取快取資料的應用程式必須具有完全信任;具有部分信任的 Web 應用程式無法插入、取出或變更在 Office 檔中快取的資料。

 資料快取可透過類別的屬性所公開的集合階層來存取 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> ：

- 屬性會傳回 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> ，其中包含檔層級自訂中的所有快取資料。

- 每個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> 皆包含一或多個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 物件。 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含在單一類別內定義的所有快取資料物件。

- 每個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 皆包含一或多個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 物件。 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>代表單一快取的資料物件。

  下列程式碼範例示範如何存取 `Sheet1` Excel 活頁簿專案類別中的快取字串。 這個範例是針對方法所提供之較大範例的一部分 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 。

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>修改快取中的資料
 若要修改快取的資料物件，您通常會執行下列步驟：

1. 將快取物件的 XML 表示還原序列化為物件的新實例。 您可以使用代表快取 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 資料物件之的屬性來存取 XML <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 。

2. 進行此複本的變更。

3. 使用下列其中一個選項，將已變更的物件序列化回資料快取：

    - 如果您想要自動序列化變更，請使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法。 這個方法會使用 **DiffGram** 格式 <xref:System.Data.DataSet> ，在資料快取中序列化、 <xref:System.Data.DataTable> 和具類型的資料集物件。 **DiffGram** 格式可確保離線檔中資料快取的變更會正確地傳送至伺服器。

    - 如果您想要執行自己的序列化來變更快取的資料，您可以直接寫入 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 屬性。 如果您使用 <xref:System.Data.Common.DataAdapter> 來更新資料庫，並在、或具類型的資料集中對資料進行變更，請指定 DiffGram 格式 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 。 否則， <xref:System.Data.Common.DataAdapter> 將會藉由加入新的資料列，而不是修改現有的資料列來更新資料庫。

### <a name="modify-data-without-deserializing-the-current-value"></a>修改資料，而不還原序列化目前的值
 在某些情況下，您可能會想要修改快取物件的值，而不需要先還原序列化目前的值。 例如，如果您要變更具有簡單類型的物件值（例如字串或整數），或在伺服器上的檔中初始化快取，就可以這樣做 <xref:System.Data.DataSet> 。 在這些情況下，您可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法，而不需要先還原序列化快取物件的目前值。

 下列程式碼範例示範如何在 Excel 活頁簿專案的類別中變更快取字串的值 `Sheet1` 。 這個範例是針對方法所提供之較大範例的一部分 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 。

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>修改資料快取中的 null 值
 儲存並關閉檔時，資料快取不會儲存具有 **null** 值的物件。 當您修改快取資料時，這項限制會有數個結果：

- 如果您將資料快取中的任何物件設定為 **null** 值，則當檔開啟時，資料快取中的所有物件都會自動設為 **null** ，而且在儲存和關閉檔時，將會清除整個資料快取。 也就是說，所有快取的物件都會從資料快取中移除，而且 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 集合將會是空的。

- 如果您在資料快取中建立具有 **null** 物件的方案，而您想要在 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 第一次開啟檔之前使用類別初始化這些物件，您必須確定已初始化資料快取中的所有物件。 如果您只初始化部分物件，當檔開啟時，所有物件都會設為 **null** ，而且在儲存和關閉檔時，會清除整個資料快取。

## <a name="access-typed-datasets-in-the-cache"></a>存取快取中具類型的資料集
 如果您想要從 Office 方案和 Office 外部的應用程式（例如 Windows Forms 應用程式或專案）存取具類型資料集中的資料， [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 您必須在兩個專案中所參考的個別元件中定義具類型的資料集。 如果您使用 [ **資料來源** 設定] wizard 或 **DataSet 設計工具**，將具類型的資料集加入至每個專案，則 .NET Framework 會將兩個專案中的具類型資料集視為不同的類型。 如需建立具類型資料集的詳細資訊，請參閱 [在 Visual Studio 中建立及設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [檔層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)