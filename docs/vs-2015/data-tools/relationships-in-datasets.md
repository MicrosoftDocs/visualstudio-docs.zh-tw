---
title: 資料集中的關聯性 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652891"
---
# <a name="relationships-in-datasets"></a>資料集中的關聯性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含相關資料表的資料集會使用 <xref:System.Data.DataRelation> 物件來代表資料表之間的父/子關聯性，並傳回彼此相關的記錄。 使用 [**資料來源設定] [Wizard]** 或 [ **DataSet 設計工具**] 將相關資料表加入至資料集時，會為您建立並設定 <xref:System.Data.DataRelation> 物件。

 @No__t_0 物件會執行兩個功能：

- 它可以提供與您正在使用之記錄相關的記錄。 如果您是在父記錄（<xref:System.Data.DataRow.GetChildRows%2A>）中，如果您使用的是子記錄（<xref:System.Data.DataRow.GetParentRow%2A>），它會提供子記錄。

- 它可以強制執行參考完整性的條件約束，例如刪除父記錄時，刪除相關的子記錄。

  請務必瞭解真正聯結與 <xref:System.Data.DataRelation> 物件的函式之間的差異。 在真正的聯結中，會從父系和子資料工作表取得記錄，並放入單一的一般記錄集。 當您使用 <xref:System.Data.DataRelation> 物件時，不會建立任何新的記錄集。 取而代之的是，DataRelation 會追蹤資料表之間的關聯性，並讓父系和子記錄保持同步。

## <a name="datarelation-objects-and-constraints"></a>DataRelation 物件和條件約束
 @No__t_0 物件也會用來建立和強制執行下列條件約束：

- Unique 條件約束，可確保資料表中的資料行不包含重複專案。

- 外鍵條件約束，可用來維護資料集中的父資料表與子資料工作表之間的參考完整性。

  您在 <xref:System.Data.DataRelation> 物件中指定的條件約束會藉由自動建立適當的物件或設定屬性來執行。 如果您使用 <xref:System.Data.DataRelation> 物件建立外鍵條件約束，則 <xref:System.Data.ForeignKeyConstraint> 類別的實例會加入至 <xref:System.Data.DataRelation> 物件的 <xref:System.Data.DataRelation.ChildKeyConstraint%2A> 屬性。

  唯一的條件約束會藉由直接將資料行的 <xref:System.Data.DataColumn.Unique%2A> 屬性設定為 `true`，或將 <xref:System.Data.UniqueConstraint> 類別的實例加入至 <xref:System.Data.DataRelation> 物件的 <xref:System.Data.DataRelation.ParentKeyConstraint%2A> 屬性來執行。 如需暫停資料集中之條件約束的詳細資訊，請參閱[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。

### <a name="referential-integrity-rules"></a>參考完整性規則
 做為外鍵條件約束的一部分，您可以指定套用於三個點的參考完整性規則：

- 當父記錄更新時

- 刪除父記錄時

- 接受或拒絕變更時

  您可以建立的規則會在 <xref:System.Data.Rule> 列舉中指定，並列在下表中。

|外鍵條件約束規則|Action|
|----------------------------------|------------|
|<xref:System.Data.Rule>|對父記錄所做的變更（更新或刪除）也會在子資料工作表的相關記錄中進行。|
|<xref:System.Data.Rule>|子記錄不會被刪除，但是子記錄中的外鍵會設定為 <xref:System.DBNull>。 使用此設定時，子記錄可以保留為「孤立」，也就是說，它們與父記錄沒有任何關聯性。 **注意：** 使用此規則可能會導致子資料工作表中的資料無效。|
|<xref:System.Data.Rule>|相關子記錄中的外鍵會設定為其預設值（由資料行的 <xref:System.Data.DataColumn.DefaultValue%2A> 屬性所建立）。|
|<xref:System.Data.Rule>|相關的子記錄不會進行任何變更。 使用此設定時，子記錄可以包含無效父記錄的參考。|

 如需有關資料集資料表中更新的詳細資訊，請參閱[將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。

### <a name="constraint-only-relations"></a>僅限條件約束關聯
 當您建立 <xref:System.Data.DataRelation> 物件時，您可以選擇指定只使用此關聯來強制執行條件約束，也就是說，它也不會用來存取相關的記錄。 您可以使用此選項來產生稍微提高效率的資料集，且包含的方法比相關記錄功能少一種。 不過，您將無法存取相關的記錄。 例如，僅限條件約束關聯可讓您無法刪除仍然具有子記錄的父記錄，而且您無法透過父系存取子記錄。

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>在 DataSet 設計工具中手動建立資料關聯
 當您使用 Visual Studio 中的資料設計工具建立資料表時，如果可以從資料來源收集資訊，就會自動建立關聯性。 如果您從 [**工具箱**] 的 [**資料集**] 索引標籤手動新增資料表，您可能必須手動建立關聯性。 如需以程式設計方式建立 <xref:System.Data.DataRelation> 物件的詳細資訊，請參閱[加入 datarelation](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)。

 資料表之間的關聯性會顯示為**DataSet 設計工具**中的行，以及描述關聯性一對多層面的索引鍵和無限大字元。 根據預設，relationshipCommentEnd Id = ' 1c8c78e19b7fa441 ' 的名稱不會出現在設計介面上。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>若要建立兩個數據表之間的關聯性

1. 在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[如何：在 DataSet 設計工具 ](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3) 中開啟資料集。

2. 將 [**關聯**性] 物件從 [**資料集**工具箱] 拖曳至關聯性中的子資料工作表。

     [**關聯**] 對話方塊隨即開啟，並在**子資料工作表**方塊中填入您將**關聯**性物件拖曳至其中的資料表。

3. 從 [**父資料表**] 方塊中選取父資料表。 父資料表包含一對多關聯性的「一」端記錄。

4. 確認**子**資料表中顯示的是正確的子資料工作表。 子資料工作表包含一對多關聯性的「多」端記錄。

5. 在 [**名稱**] 方塊中輸入關聯性的名稱，或保留以選取的資料表為基礎的預設名稱。 這是程式碼中實際 <xref:System.Data.DataRelation> 物件的名稱。

6. 在 [索引**鍵資料行**] 和 [**外鍵資料行**] 清單中，選取聯結資料表的資料行。

7. 選取要建立關聯性、條件約束或兩者。 如需相關資訊，請參閱[DataRelation 物件簡介](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)。

8. 選取或清除 [**嵌套關聯**] 方塊。 選取此選項會將 [<xref:System.Data.DataRelation.Nested%2A>] 屬性設定為 [`true`]，而當這些資料列寫入為 XML 資料或與 <xref:System.Xml.XmlDataDocument> 同步處理時，它會讓關聯的子資料列嵌套在父資料行中。 如需詳細資訊，請參閱 <<c0>嵌套 datarelation。

9. 設定當您對這些資料表中的記錄進行變更時，所要強制執行的規則。 如需詳細資訊，請參閱<xref:System.Data.Rule>。

10. 按一下 **[確定]** 以建立關聯性。 關聯線會出現在這兩個數據表的設計工具上。

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>若要在 DataSet 設計工具中顯示關聯名稱

1. 在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[如何：在 DataSet 設計工具 ](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3) 中開啟資料集。

2. 從 [**資料**] 功能表中，選取 [**顯示關聯標籤**] 命令以顯示關聯名稱。 清除該命令以隱藏關聯名稱。
