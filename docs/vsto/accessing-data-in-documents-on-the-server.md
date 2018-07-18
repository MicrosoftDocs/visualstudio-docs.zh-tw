---
title: 存取伺服器上的文件中的資料
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecfebda02096d1a36a5de84919aad65482a25ec0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268378"
---
# <a name="access-data-in-documents-on-the-server"></a>存取伺服器上的文件中的資料
  您可以程式設計的文件層級自訂中的資料，而不需要使用 Microsoft Office Word 或 Microsoft Office Excel 物件模型。 這表示您可以存取並沒有文字的伺服器上的文件中所包含的資料，或安裝 Excel。 例如，程式碼在伺服器上 (例如，在[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面) 可以自訂文件中的資料，並將自訂文件傳送給終端使用者。 當使用者開啟文件時，方案組件中的資料繫結程式碼將自訂的資料繫結至文件。 這可能是因為文件中的資料分開的使用者介面。 如需詳細資訊，請參閱[文件層級自訂中快取資料](../vsto/cached-data-in-document-level-customizations.md)。  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>快取伺服器上使用的資料  
 若要快取文件中的資料物件，請將標記與<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>屬性在設計階段，或使用`StartCaching`在執行階段將主項目的的方法。 當您快取文件中的資料物件[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]將物件序列化成 XML 字串是儲存在文件中。 物件必須符合特定需求，才能進行快取。 如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  

 伺服器端程式碼可以使用操作資料快取中的任何資料物件。 快取的資料執行個體繫結的控制項與同步處理使用者介面，使資料所做的任何伺服器端變更時自動顯示在用戶端上開啟文件。  

## <a name="access-data-in-the-cache"></a>存取快取中的資料  
 您可以從辦公室外部的應用程式，例如從主控台應用程式、 Windows Forms 應用程式或網頁存取快取中的資料。 存取快取的資料的應用程式必須有完全信任。部分信任的 Web 應用程式無法插入、 擷取或變更快取 Office 文件中的資料。  

 資料快取是透過使用集合的階層架構所公開的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別：  

-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性會傳回<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>，其中包含所有文件層級自訂中快取的資料。  

-   每個<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>包含一或多個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>物件。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含的所有快取的資料物件定義在單一類別中。  

-   每個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>包含一或多個<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>物件。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>代表單一快取的資料物件。  

 下列程式碼範例示範如何存取快取中的字串`Sheet1`的 Excel 活頁簿專案的類別。 這個範例是所提供之較大範例的一部分<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>修改快取中的資料  
 若要修改的快取的資料物件，您通常會執行下列步驟：  

1.  還原序列化之物件的新執行個體的快取物件的 XML 表示。 您可以使用來存取 XML<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>表示快取的資料物件。  

2.  這個複本中進行變更。  

3.  序列化回資料快取的已變更的物件，使用下列選項的其中一個：  

    -   如果您想要自動序列化所做的變更，使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法。 這個方法會使用**DiffGram**格式序列化<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，及型別的資料快取中的資料集物件。 **DiffGram**格式，可確保離線的文件中的資料快取的變更會正確地傳送至伺服器。  

    -   如果您想要變更快取資料執行您自己的序列化，您可以撰寫直接<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>屬性。 指定**DiffGram**格式化，如果您使用<xref:System.Data.Common.DataAdapter>以更新資料庫中的資料所做的變更<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或輸入資料集。 否則，<xref:System.Data.Common.DataAdapter>會加入新的資料列，而不修改現有的資料列來更新資料庫。  

### <a name="modify-data-without-deserializing-the-current-value"></a>修改資料，但不還原序列化的目前值  
 在某些情況下，您可能要修改的快取的物件值，而不會先還原序列化的目前值。 例如，您可以如果您要變更物件具有簡單型別，例如字串或整數值，或如果您要初始化快取<xref:System.Data.DataSet>在伺服器上的文件中。 在這些情況下，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法，而不先還原序列化的快取物件的目前值。  

 下列程式碼範例示範如何變更快取中之字串值`Sheet1`的 Excel 活頁簿專案的類別。 這個範例是所提供之較大範例的一部分<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>方法。  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>修改資料快取中的 null 值  
 資料快取不會儲存物件具有值**null**時儲存並關閉文件。 當您修改快取的資料時，這項限制會有數個結果：  

-   如果您在資料快取的值中設定任何物件**null**，所有資料快取中的物件將會自動設定為**null**當文件開啟時，與整個資料快取都將清除的時機儲存並關閉文件。 也就是說，所有快取的物件會移除資料快取和<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>會空的集合。  

-   如果您要建置在方案中的使用**null**物件資料快取，以及您想要初始化這些物件是使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>第一次開啟文件之前的類別時，您必須確定您的所有物件初始化中的資料快取中。 如果您初始化只對某些物件時，所有的物件將設定為**null**當文件開啟時，並將清除整個資料快取，儲存和關閉文件時。  

## <a name="access-typed-datasets-in-the-cache"></a>存取快取中具類型資料集  
 如果您想要存取中具類型資料集的資料，同時從 Office 方案和 Office，外面的應用程式，例如 Windows Forms 應用程式或[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]專案中，您必須同時參考其他組件中定義具類型資料集專案。 如果您將具類型資料集加入每個專案使用**資料來源組態**精靈或**Dataset 設計工具**，.NET Framework 會將具類型資料集做為不同類型的兩個專案中. 如需建立具類型資料集的詳細資訊，請參閱[建立並設定 Visual Studio 中的資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。  

## <a name="see-also"></a>另請參閱  
 [存取伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)   
 [在文件層級自訂中快取的資料](../vsto/cached-data-in-document-level-customizations.md)  
