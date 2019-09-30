---
title: 存取伺服器上檔中的資料
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ab033120c0913bbae33458c5a2d0b53972364581
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255771"
---
# <a name="access-data-in-documents-on-the-server"></a>存取伺服器上檔中的資料
  您可以針對檔層級自訂中的資料進行程式設計，而不需要使用 Microsoft Office Word 或 Microsoft Office Excel 的物件模型。 這表示您可以存取未安裝 Word 或 Excel 之伺服器上的檔中所包含的資料。 例如，伺服器上的程式碼（例如，在[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面中）可以自訂檔中的資料，並將自訂的檔傳送給使用者。 當使用者開啟檔時，方案元件中的資料系結程式碼會將自訂資料系結至檔。 這是可能的，因為檔中的資料是與使用者介面分開。 如需詳細資訊，請參閱[檔層級自訂中的](../vsto/cached-data-in-document-level-customizations.md)快取資料。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>要在伺服器上使用的快取資料
 若要快取檔中的資料物件，請在設計<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>時間將它標記為屬性，或`StartCaching`在執行時間使用主專案的方法。 當您快取檔中的資料物件時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]會將物件序列化為儲存在檔中的 XML 字串。 物件必須符合特定需求，才能符合快取的資格。 如需詳細資訊，請參閱快取[資料](../vsto/caching-data.md)。

 伺服器端程式碼可以運算元據快取中的任何資料物件。 系結至快取資料實例的控制項會與使用者介面同步處理，以便在用戶端上開啟檔時，自動顯示對資料所做的任何伺服器端變更。

## <a name="access-data-in-the-cache"></a>存取快取中的資料
 您可以從 Office 外部的應用程式存取快取中的資料，例如從主控台應用程式、Windows Forms 應用程式或網頁。 存取快取資料的應用程式必須有完全信任;具有部分信任的 Web 應用程式無法插入、抓取或變更在 Office 檔中快取的資料。

 資料快取可透過<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別的屬性所公開的集合階層來存取：

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性會傳回，其中包含檔層級自訂中的<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>所有快取資料。

- 每<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>個都包含一<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>或多個物件。 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含在單一類別內定義的所有快取資料物件。

- 每<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>個都包含一<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>或多個物件。 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>代表單一快取資料物件。

  下列程式碼範例示範如何存取 Excel 活頁簿專案之`Sheet1`類別中的快取字串。 這個範例是針對<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法所提供之較大範例的一部分。

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>修改快取中的資料
 若要修改快取的資料物件，您通常會執行下列步驟：

1. 將快取物件的 XML 表示還原序列化為物件的新實例。 您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>代表快取資料物件<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>之的屬性來存取 XML。

2. 對此複本進行變更。

3. 使用下列其中一個選項，將已變更的物件序列化回資料快取：

    - 如果您想要自動序列化變更，請使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法。 這個方法會使用**DiffGram**格式<xref:System.Data.DataSet>，在資料<xref:System.Data.DataTable>快取中序列化、和具類型的資料集物件。 **DiffGram**格式可確保離線檔中資料快取的變更會正確地傳送至伺服器。

    - 如果您想要針對快取資料的變更執行自己的序列化，您可以直接<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>寫入屬性（property）。 如果您使用<xref:System.Data.Common.DataAdapter>來更新資料庫<xref:System.Data.DataSet>，其中包含對、或具類型資料集之資料所做<xref:System.Data.DataTable>的變更，請指定**DiffGram**格式。 否則， <xref:System.Data.Common.DataAdapter>將會藉由加入新的資料列來更新資料庫，而不是修改現有的資料列。

### <a name="modify-data-without-deserializing-the-current-value"></a>修改資料而不還原序列化目前的值
 在某些情況下，您可能想要修改快取物件的值，而不需要先還原序列化目前的值。 例如，如果您要變更具有簡單類型（例如字串或整數）之物件的值，或在伺服器上的檔<xref:System.Data.DataSet>中初始化快取，則可以執行此動作。 在這些情況下，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法，而不需要先還原序列化快取物件的目前值。

 下列程式碼範例示範如何在 Excel 活頁簿專案的`Sheet1`類別中變更快取字串的值。 這個範例是針對<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法所提供之較大範例的一部分。

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>修改資料快取中的 null 值
 儲存和關閉檔時，資料快取不會儲存具有**null**值的物件。 當您修改快取資料時，這項限制會有數個結果：

- 如果您將資料快取中的任何物件設定為**null**值，則在檔開啟時，資料快取中的所有物件都會自動設定為**null** ，而且在儲存和關閉檔時，將會清除整個資料快取。 也就是說，所有快取的物件都會從資料快取中移除，而且集合會<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>是空的。

- 如果您在資料快取中建立具有**null**物件的方案，而您想要在第一次<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>開啟檔之前使用類別來初始化這些物件，您必須確定已初始化資料快取中的所有物件。 如果您只初始化部分物件，當檔開啟時，所有物件都會設定為**null** ，而且在儲存和關閉檔時，會清除整個資料快取。

## <a name="access-typed-datasets-in-the-cache"></a>存取快取中的具類型資料集
 如果您想要從 office 方案和 office 外部的應用程式（例如 Windows Forms 應用程式或[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]專案）存取具類型資料集中的資料，您必須在兩個參考的個別元件中定義具類型的資料集投影. 如果您使用 [**資料來源**設定向導] 或**DataSet 設計工具**，將具類型的資料集加入至每個專案，則 .NET Framework 會將這兩個專案中的具類型資料集視為不同的類型。 如需建立具類型資料集的詳細資訊，請參閱[在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [存取伺服器上檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [檔層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)