---
title: "用來建立資料集之間的關聯性的 DataRelation |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bfc537118f6c1769ec98893099daa0c61d1b5b1d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="create-relationships-between-datasets"></a>建立資料集之間的關聯性
包含相關的資料的資料集資料表會使用<xref:System.Data.DataRelation>代表資料表之間的父子式關聯性，並傳回相關的記錄從另一個物件。 相關的資料表加入至資料集，利用**資料來源組態精靈**，或**Dataset 設計工具**，建立以及設定<xref:System.Data.DataRelation>為您的物件。  
  
<xref:System.Data.DataRelation>物件會執行兩個函式：  
  
-   它可以讓使用與您正在使用記錄相關的記錄。 如果您是在父記錄，它會提供子記錄 (<xref:System.Data.DataRow.GetChildRows%2A>) 和父記錄，如果您正在使用子記錄 (<xref:System.Data.DataRow.GetParentRow%2A>)。  
  
-   它可以強制執行參考完整性，例如當您刪除父記錄，請刪除相關的子記錄的條件約束。  
  
請務必了解，則為 true 的聯結與函式之間的差異<xref:System.Data.DataRelation>物件。 在真正的聯結，記錄是取自父和子資料表，並放入一個單一的一般資料錄集。 當您使用<xref:System.Data.DataRelation>物件時，會建立任何新資料錄集。 相反地，DataRelation 追蹤資料表之間的關聯性，並保留父和子記錄保持同步。  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation 物件和條件約束  
A<xref:System.Data.DataRelation>物件也可用來建立和強制執行下列條件約束：  
  
-   Unique 條件約束，以確保資料表中的資料行包含沒有重複項目。  
  
-   Foreign key 條件約束，可用於維護資料集內的父和子資料表之間的參考完整性。  
  
您在中指定的條件約束<xref:System.Data.DataRelation>物件由自動建立適當的物件或設定屬性。 如果您建立外部索引鍵條件約束使用<xref:System.Data.DataRelation>物件、 執行個體的<xref:System.Data.ForeignKeyConstraint>類別會加入至<xref:System.Data.DataRelation>物件的<xref:System.Data.DataRelation.ChildKeyConstraint%2A>屬性。  
  
會實作 unique 條件約束只需設定<xref:System.Data.DataColumn.Unique%2A>屬性的資料行，以`true`或新增的執行個體<xref:System.Data.UniqueConstraint>類別<xref:System.Data.DataRelation>物件的<xref:System.Data.DataRelation.ParentKeyConstraint%2A>屬性。 上暫停資料集內的條件約束的資訊，請參閱[填入 dataset 時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
### <a name="referential-integrity-rules"></a>參考完整性  
外部索引鍵條件約束的一部份，您可以指定在三個點所套用的參考完整性：  
  
-   當更新父記錄  
  
-   當刪除父記錄  
  
-   當變更已接受或拒絕  
  
中指定的規則，您可以進行<xref:System.Data.Rule>列舉型別與會列在下表。  
  
|外部索引鍵條件約束規則|動作|  
|----------------------------------|------------|  
|<xref:System.Data.Rule.Cascade>|父記錄所做的變更 （更新或刪除） 也會是子資料表中的相關記錄。|  
|<xref:System.Data.Rule.SetNull>|不會刪除子記錄，但子記錄的外部索引鍵設定為<xref:System.DBNull>。 使用此設定時，子記錄可以保留為 「 處理 」，亦即有沒有父資料錄的關聯性。 **注意：**使用這項規則可能會導致子資料表中的資料無效。|  
|<xref:System.Data.Rule.SetDefault>|相關的子記錄的外部索引鍵設定為預設值 (如同建立的資料行所<xref:System.Data.DataColumn.DefaultValue%2A>屬性)。|  
|<xref:System.Data.Rule.None>|不會變更相關的子記錄。 使用此設定時，子記錄可能包含無效的父記錄的參考。|  
  
如需有關資料集資料表中更新的詳細資訊，請參閱[將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。  
  
### <a name="constraint-only-relations"></a>僅條件約束的關聯性  
當您建立<xref:System.Data.DataRelation>物件，您必須指定的關聯性只能用來強制執行條件約束的選項，也就是說，它將不也可用來存取相關的記錄。 您可以使用此選項來產生稍微更有效率，且其中包含比具有相關記錄功能的方法較少的資料集。 不過，您將無法存取相關的記錄。 例如，僅條件約束的關聯可防止您刪除父記錄，仍有子記錄，而且您無法透過父存取子記錄。  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>手動建立 Dataset 設計工具中的資料關聯性  
當您使用 Visual Studio 中的 資料設計工具建立資料的資料表時，會自動建立關聯性若從來源資料的蒐集的資訊。 如果您手動加入資料表，從**資料集** 索引標籤**工具箱**，您可能必須手動建立關聯性。 如需建立資訊<xref:System.Data.DataRelation>物件以程式設計的方式，請參閱[加入 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)。  
  
資料表之間的關聯性顯示為中的行**Dataset 設計工具**，以用來描述一對多關聯性層面的索引鍵和無限大圖像。 根據預設，關聯性名稱不會不會出現在設計介面上。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>若要建立兩個資料表之間的關聯性  
  
1.  開啟您的資料集在**Dataset 設計工具**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  拖曳**關聯**物件從**資料集**工具箱 拖曳到關聯性中的子資料表。  
  
     **關聯**對話方塊隨即開啟，填入**子資料表**方塊與您拖曳至資料表**關聯**到物件。  
  
3.  選取從父資料表**父資料表**方塊。 父資料表包含資料錄一對多關聯性的 「 一 」 端。  
  
4.  確認正確的子資料表會顯示在**子資料表**方塊。 子資料表包含資料錄一對多關聯性的 「 多 」 端。  
  
5.  輸入的名稱中的關聯性**名稱**方塊中，或保留預設名稱，根據選取的資料表。 這是實際名稱<xref:System.Data.DataRelation>程式碼中的物件。  
  
6.  選取聯結的資料表中的資料行**索引鍵資料行**和**外部索引鍵資料行**列出。  
  
7.  選取是否要建立關聯性、 條件約束，或兩者。   
  
8.  選取或清除**巢狀關聯**方塊。 選取這個選項會設定<xref:System.Data.DataRelation.Nested%2A>屬性`true`，這會使子資料列時寫為 XML 資料或與同步處理這些資料列的父資料行內巢狀關聯性的<xref:System.Xml.XmlDataDocument>。 如需詳細資訊，請參閱[巢狀 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)。  
  
9. 設定您正在變更這些資料表中的記錄時，強制執行規則。 如需詳細資訊，請參閱<xref:System.Data.Rule>。  
  
10. 按一下**確定**建立關聯性。 關聯線會出現在兩個資料表之間的設計工具。  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>若要在 Dataset 設計工具中顯示關聯名稱  
  
1.  開啟您的資料集在**Dataset 設計工具**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  從**資料**功能表上，選取**顯示關聯性標籤**命令，以顯示關聯性名稱。 清除該命令可以隱藏關聯名稱。

## <a name="see-also"></a>請參閱
[在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)