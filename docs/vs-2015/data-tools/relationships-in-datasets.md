---
title: 在資料集中的關聯性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9d2c2c6f178c952a5516533c2722bc451be2e3bf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649663"
---
# <a name="relationships-in-datasets"></a>在資料集中的關聯性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含相關的資料的資料集資料表會使用<xref:System.Data.DataRelation>物件代表資料表之間的父子式關聯性，以及從另一個傳回相關的記錄。 相關的資料表加入資料集，使用**資料來源組態精靈**，或有**Dataset 設計工具**，建立以及設定<xref:System.Data.DataRelation>為您的物件。  
  
 <xref:System.Data.DataRelation>物件會執行兩個函式：  
  
- 它可讓您正在使用的記錄相關的記錄。 如果您是在父記錄，它會提供子記錄 (<xref:System.Data.DataRow.GetChildRows%2A>) 和父記錄，如果您正在使用子記錄 (<xref:System.Data.DataRow.GetParentRow%2A>)。  
  
- 它可以強制執行參考完整性，例如當您刪除父記錄，請刪除相關的子記錄的條件約束。  
  
  請務必了解真正的聯結與函式之間的差異<xref:System.Data.DataRelation>物件。 在真正的聯結，是取自父和子資料表的記錄，並將其放入單一的一般資料錄集中。 當您使用<xref:System.Data.DataRelation>物件時，會建立任何新資料錄集。 DataRelation 會追蹤資料表之間的關聯性而保留父和子記錄保持同步。  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation 物件和條件約束  
 A<xref:System.Data.DataRelation>物件也可用來建立和強制執行下列條件約束：  
  
- Unique 條件約束，保證可直接存取資料表的資料行包含不重複的項目。  
  
- Foreign key 條件約束，可用來維護參考資料集中的父和子資料表之間的完整性。  
  
  您在中指定的條件約束<xref:System.Data.DataRelation>物件由自動建立適當的物件，或設定屬性。 如果您使用建立的外部索引鍵條件約束<xref:System.Data.DataRelation>物件、 執行個體的<xref:System.Data.ForeignKeyConstraint>類別會新增至<xref:System.Data.DataRelation>物件的<xref:System.Data.DataRelation.ChildKeyConstraint%2A>屬性。  
  
  會實作 unique 條件約束只設定<xref:System.Data.DataColumn.Unique%2A>屬性的資料行，以`true`，或加入的執行個體<xref:System.Data.UniqueConstraint>類別<xref:System.Data.DataRelation>物件的<xref:System.Data.DataRelation.ParentKeyConstraint%2A>屬性。 如需暫停資料集內的條件約束資訊，請參閱[填入 dataset 時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
### <a name="referential-integrity-rules"></a>參考完整性規則  
 外部索引鍵條件約束的一部份，您可以指定在三個點所套用的參考完整性規則：  
  
- 當更新父記錄  
  
- 當刪除父記錄  
  
- 當接受或拒絕變更  
  
  中指定的規則，您可以進行<xref:System.Data.Rule>列舉型別和是下表所列。  
  
|外部索引鍵條件約束規則|動作|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|父記錄所做的變更 （更新或刪除） 也會在子資料表中的相關記錄。|  
|<xref:System.Data.Rule>|不會刪除子記錄，但是子記錄的外部索引鍵設定為<xref:System.DBNull>。 使用此設定，子記錄可保持為 「 孤立 」 — 也就是它們有沒有父資料錄的關聯性。 **注意：** 使用這項規則，可能會導致子資料表中有無效的資料。|  
|<xref:System.Data.Rule>|相關的子記錄的外部索引鍵設為其預設值 (由資料行建立<xref:System.Data.DataColumn.DefaultValue%2A>屬性)。|  
|<xref:System.Data.Rule>|不會變更相關的子記錄。 使用此設定，子記錄可包含無效的父記錄的參考。|  
  
 如需有關資料集資料表中更新的詳細資訊，請參閱[將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。  
  
### <a name="constraint-only-relations"></a>僅限條件約束的關聯性  
 當您建立<xref:System.Data.DataRelation>物件，您必須指定，將關聯只能用來強制執行條件約束的選項，也就是，它將不也可用來存取相關的記錄。 您可以使用此選項來產生資料集，這是較具效率，並包含較少的方法比具有相關記錄功能。 不過，您將無法存取相關的記錄。 例如，僅條件約束的關聯可防止您刪除仍具有子記錄的父記錄，而您無法透過父系存取子記錄。  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>以手動方式在 Dataset 設計工具中建立的資料關聯  
 當您在 Visual Studio 中使用資料設計工具建立資料的資料表時，會自動建立關聯性如果可以從您的資料來源收集的資訊。 如果您手動新增從資料表**資料集**索引標籤**工具箱**，您可能要手動建立關聯性。 如需建立資訊<xref:System.Data.DataRelation>物件以程式設計的方式，請參閱[新增 Datarelation](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)。  
  
 資料表之間的關聯性會顯示為中的線條**Dataset 設計工具**，以描述關聯性的一對多層面的索引鍵和無限大圖像。 根據預設，relationshipCommentEnd 識別碼名稱 = '1c8c78e19b7fa441' 未出現在設計介面。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>若要建立兩個資料表之間的關聯性  
  
1.  在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[如何：在 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  拖曳**關聯**物件**DataSet**工具箱拖曳到關聯性中的子資料表。  
  
     **關聯** 對話方塊隨即開啟，填入**子資料表**方塊，與您拖曳資料表**關聯**物件。  
  
3.  選取從父資料表**父資料表** 方塊中。 父資料表包含一對多關聯性的 「 一 」 端上的記錄。  
  
4.  確認正確的子資料表會顯示在**子資料表** 方塊中。 子資料表包含一對多關聯性的 「 多 」 端上的記錄。  
  
5.  輸入的名稱中的關聯性**名稱**方塊中，或保留預設名稱，根據選取的資料表。 這是實際名稱<xref:System.Data.DataRelation>在程式碼中的物件。  
  
6.  選取聯結的資料表中的資料行**索引鍵資料行**並**外部索引鍵資料行**列出。  
  
7.  選取是否要建立關聯性、 條件約束，或兩者。 如需資訊，請參閱[DataRelation 物件簡介](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)。  
  
8.  選取或清除**巢狀關聯** 方塊中。 選取這個選項會設定<xref:System.Data.DataRelation.Nested%2A>屬性，以`true`，這會使子資料列時寫為 XML 資料或與同步處理這些資料列的父資料行內巢狀關聯性的<xref:System.Xml.XmlDataDocument>。 如需詳細資訊，請參閱 <<c0> [ 巢狀 Datarelation](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab)。  
  
9. 設定您要對這些資料表中的記錄進行變更時強制執行規則。 如需詳細資訊，請參閱<xref:System.Data.Rule>。  
  
10. 按一下 **確定**建立關聯性。 關聯線會顯示兩個資料表之間的設計工具上。  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>若要在 Dataset 設計工具中顯示關聯性名稱  
  
1.  在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[如何：在 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  從**資料**功能表上，選取**顯示關聯性標籤**命令，以顯示關聯性名稱。 清除該命令可以隱藏的關聯性名稱。
