---
title: 存取伺服器上的文件中的資料
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
ms.openlocfilehash: d12c8168ef01dd3a38616af4f9dab2c38662bfff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563102"
---
# <a name="access-data-in-documents-on-the-server"></a>存取伺服器上的文件中的資料
  您可以程式對文件層級自訂中的資料，而不需要使用 Microsoft Office Word 或 Microsoft Office Excel 物件模型。 這表示您可以存取並沒有文字的伺服器上的文件中包含的資料，或安裝 Excel。 例如，程式碼的伺服器上 (例如，在[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面) 可以自訂文件中的資料，並將自訂的文件傳送給使用者。 當使用者開啟文件時，方案組件中的資料繫結程式碼將自訂的資料繫結到文件。 這可能是因為文件中的資料分開的使用者介面。 如需詳細資訊，請參閱 <<c0> [ 快取文件層級自訂中的資料](../vsto/cached-data-in-document-level-customizations.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>在伺服器上使用的快取資料
 快取文件中的資料物件，將它與標示<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>在設計階段屬性，或者使用`StartCaching`方法在執行階段的主項目。 當您快取文件中的資料物件[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]將物件序列化成 XML 字串儲存在文件中。 物件必須符合特定需求，使其適用於快取。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。

 伺服器端程式碼可以操作資料快取中的任何資料物件。 快取的資料執行個體繫結的控制項與同步處理使用者介面，以便對資料進行的任何伺服器端變更時自動顯示在用戶端上開啟文件。

## <a name="access-data-in-the-cache"></a>存取快取中的資料
 您可以從辦公室，之外的應用程式，例如從主控台應用程式、 Windows Form 應用程式或網頁存取快取中的資料。 存取快取的資料的應用程式必須有完全信任;部分信任的 Web 應用程式無法插入、 擷取，或變更快取 Office 文件中的資料。

 資料快取是透過集合所公開的階層架構存取<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別：

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性會傳回<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>，其中包含所有文件層級自訂中快取的資料。

- 每個<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>包含一或多個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>物件。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含的所有快取的資料物件的單一類別內所定義的。

- 每個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含一或多個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>物件。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>代表單一快取的資料物件。

  下列程式碼範例示範如何存取中的快取的字串`Sheet1`類別的 Excel 活頁簿專案。 這個範例是供較大範例的一部分<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>修改快取中的資料
 若要修改的快取的資料物件，您通常會執行下列步驟：

1. 還原序列化物件的新執行個體的快取物件的 XML 表示。 您可以使用來存取 XML<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>表示快取的資料物件。

2. 這個複本中進行變更。

3. 序列化回資料快取的已變更的物件，使用下列選項之一：

    - 如果您想要自動序列化所做的變更，使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法。 這個方法會使用**DiffGram**序列化格式<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，以及型別資料快取中的資料集物件。 **DiffGram**格式可確保離線的文件中的資料快取的變更會正確地傳送到伺服器。

    - 如果您想要執行您自己的序列化，對快取的資料變更，您可以直接寫到<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>屬性。 指定**DiffGram**時，您使用格式化<xref:System.Data.Common.DataAdapter>中的資料所做的變更更新資料庫<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或輸入資料集。 否則，<xref:System.Data.Common.DataAdapter>會藉由新增新的資料列，而非修改現有的資料列更新資料庫。

### <a name="modify-data-without-deserializing-the-current-value"></a>修改資料，而不會還原序列化目前的值
 在某些情況下，您可能想要修改的快取的物件值，而不先還原序列化目前的值。 例如，您可以這樣做您要變更的物件，具有簡單的型別，例如字串或整數值，或如果您要初始化快取<xref:System.Data.DataSet>在伺服器上的文件中。 在這些情況下，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法，而不先還原序列化目前的快取的物件值。

 下列程式碼範例示範如何變更快取的字串中的值`Sheet1`類別的 Excel 活頁簿專案。 這個範例是供較大範例的一部分<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>修改的資料快取中的 null 值
 資料快取不會儲存物件具有值**null**時儲存並關閉文件。 當您修改快取的資料時，這項限制會有數個結果：

- 如果您在資料快取的值中設定的任何物件**null**，所有的資料快取中的物件都會自動設定為**null**當文件會開啟，而且整個資料將會清除快取的時機儲存並關閉文件。 也就是快取的物件將會移除所有資料快取，而<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>會空的集合。

- 如果您要建置的解決方案**null**物件的資料快取，以及您想要使用這些物件來初始化<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>第一次開啟文件之前的類別時，您必須確定您的所有物件初始化中的資料快取中。 如果您初始化只有部分的物件，所有的物件會設定為**null**當文件會開啟，而且儲存和關閉文件時，將會清除整個資料快取。

## <a name="access-typed-datasets-in-the-cache"></a>存取快取中具類型資料集
 如果您想要存取中具類型資料集的資料，從 Office 方案和從辦公室外面的應用程式，例如在 Windows Forms 應用程式或[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]專案中，您必須定義具類型資料集參考中的個別組件專案。 如果您加入具類型資料集所使用的每個專案**資料來源組態**精靈 或**Dataset 設計工具**，.NET Framework 會將具類型資料集做為不同類型的兩個專案中. 如需建立具類型資料集的詳細資訊，請參閱 <<c0> [ 建立和設定 Visual Studio 中的資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)
- [文件層級自訂中的快取的資料](../vsto/cached-data-in-document-level-customizations.md)