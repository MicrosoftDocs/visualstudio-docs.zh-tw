---
title: 使用 DataRelation 來建立資料集之間的關聯性
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a9d733892b3bc62c272f31b0d7cc1aa10fbf229d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586311"
---
# <a name="create-relationships-between-datasets"></a>建立資料集之間的關聯性
包含相關資料表的資料集會使用 <xref:System.Data.DataRelation> 物件來代表資料表之間的父/子關聯性，並傳回彼此相關的記錄。 使用 [**資料來源設定] [Wizard]** 或 [ **DataSet 設計工具**] 將相關資料表加入至資料集時，會為您建立並設定 <xref:System.Data.DataRelation> 物件。

<xref:System.Data.DataRelation> 物件會執行兩個功能：

- 它可以提供與您正在使用之記錄相關的記錄。 如果您是在父記錄（<xref:System.Data.DataRow.GetChildRows%2A>）中，如果您使用的是子記錄（<xref:System.Data.DataRow.GetParentRow%2A>），它會提供子記錄。

- 它可以強制執行參考完整性的條件約束，例如刪除父記錄時，刪除相關的子記錄。

請務必瞭解真正聯結與 <xref:System.Data.DataRelation> 物件的函式之間的差異。 在真正的聯結中，會從父系和子資料工作表取得記錄，並放入單一的一般記錄集。 當您使用 <xref:System.Data.DataRelation> 物件時，不會建立任何新的記錄集。 取而代之的是，DataRelation 會追蹤資料表之間的關聯性，並讓父系和子記錄保持同步。

## <a name="datarelation-objects-and-constraints"></a>DataRelation 物件和條件約束
<xref:System.Data.DataRelation> 物件也會用來建立和強制執行下列條件約束：

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
| - |------------|
|<xref:System.Data.Rule.Cascade>|對父記錄所做的變更（更新或刪除）也會在子資料工作表的相關記錄中進行。|
|<xref:System.Data.Rule.SetNull>|子記錄不會被刪除，但是子記錄中的外鍵會設定為 <xref:System.DBNull>。 使用此設定時，子記錄可以保留為「孤立」，也就是說，它們與父記錄沒有任何關聯性。 **注意：** 使用此規則可能會導致子資料工作表中的資料無效。|
|<xref:System.Data.Rule.SetDefault>|相關子記錄中的外鍵會設定為其預設值（由資料行的 <xref:System.Data.DataColumn.DefaultValue%2A> 屬性所建立）。|
|<xref:System.Data.Rule.None>|相關的子記錄不會進行任何變更。 使用此設定時，子記錄可以包含無效父記錄的參考。|

如需有關資料集資料表中更新的詳細資訊，請參閱[將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。

### <a name="constraint-only-relations"></a>僅限條件約束關聯
當您建立 <xref:System.Data.DataRelation> 物件時，您可以選擇指定只使用此關聯來強制執行條件約束，也就是說，它也不會用來存取相關的記錄。 您可以使用此選項來產生稍微提高效率的資料集，且包含的方法比相關記錄功能少一種。 不過，您將無法存取相關的記錄。 例如，僅限條件約束關聯可讓您無法刪除仍然具有子記錄的父記錄，而且您無法透過父系存取子記錄。

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>在 DataSet 設計工具中手動建立資料關聯
當您使用 Visual Studio 中的資料設計工具建立資料表時，如果可以從資料來源收集資訊，就會自動建立關聯性。 如果您從 [**工具箱**] 的 [**資料集**] 索引標籤手動新增資料表，您可能必須手動建立關聯性。 如需以程式設計方式建立 <xref:System.Data.DataRelation> 物件的詳細資訊，請參閱[加入 datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)。

資料表之間的關聯性會顯示為**DataSet 設計工具**中的行，以及描述關聯性一對多層面的索引鍵和無限大字元。 根據預設，關聯性的名稱不會出現在設計介面上。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>若要建立兩個數據表之間的關聯性

1. 在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 DataSet 設計工具](walkthrough-creating-a-dataset-with-the-dataset-designer.md)中建立資料集。

2. 將 [**關聯**性] 物件從 [**資料集**工具箱] 拖曳至關聯性中的子資料工作表。

     [**關聯**] 對話方塊隨即開啟，並在**子資料工作表**方塊中填入您將**關聯**性物件拖曳至其中的資料表。

3. 從 [**父資料表**] 方塊中選取父資料表。 父資料表包含一對多關聯性的「一」端記錄。

4. 確認**子**資料表中顯示的是正確的子資料工作表。 子資料工作表包含一對多關聯性的「多」端記錄。

5. 在 [**名稱**] 方塊中輸入關聯性的名稱，或保留以選取的資料表為基礎的預設名稱。 這是程式碼中實際 <xref:System.Data.DataRelation> 物件的名稱。

6. 在 [索引**鍵資料行**] 和 [**外鍵資料行**] 清單中，選取聯結資料表的資料行。

7. 選取要建立關聯性、條件約束或兩者。

8. 選取或清除 [**嵌套關聯**] 方塊。 選取此選項會將 [<xref:System.Data.DataRelation.Nested%2A>] 屬性設定為 [`true`]，而當這些資料列寫入為 XML 資料或與 <xref:System.Xml.XmlDataDocument>同步處理時，它會讓關聯的子資料列嵌套在父資料行中。 如需詳細資訊，請參閱 <<c0>嵌套 datarelation。

9. 設定當您對這些資料表中的記錄進行變更時，所要強制執行的規則。 如需詳細資訊，請參閱<xref:System.Data.Rule>。

10. 按一下 **[確定]** 以建立關聯性。 關聯線會出現在這兩個數據表的設計工具上。

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>若要在 DataSet 設計工具中顯示關聯名稱

1. 在 **DataSet 設計工具**中開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 DataSet 設計工具](walkthrough-creating-a-dataset-with-the-dataset-designer.md)中建立資料集。

2. 從 [**資料**] 功能表中，選取 [**顯示關聯標籤**] 命令以顯示關聯名稱。 清除該命令以隱藏關聯名稱。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
