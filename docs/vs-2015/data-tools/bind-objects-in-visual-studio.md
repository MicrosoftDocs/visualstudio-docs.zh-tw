---
title: 系結物件
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c487df5623a233146655593265e15c34a884de3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673002"
---
# <a name="bind-objects-in-visual-studio"></a>繫結 Visual Studio 中的物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 提供設計階段工具，可讓您在應用程式中使用自訂物件做為資料來源。 當您想要將資料庫中的資料儲存在您系結至 UI 控制項的物件中時，建議的方法是使用 Entity Framework 來產生類別或類別。 實體會 Frameworkautogenerates 所有的未定案變更追蹤程式碼，這表示當您在 DbSet 物件上呼叫 AcceptChanges 時，對本機物件所做的任何變更都會自動儲存至資料庫。    如需詳細資訊，請參閱[Entity Framework 檔](https://ef.readthedocs.org/en/latest/)。

> [!TIP]
> 只有在您的應用程式已根據資料集時，才應該考慮本文中的物件系結方法。如果您已經熟悉資料集，也可以使用這些方法，而您將處理的資料是表格式，而且不太複雜或太大。 如需更簡單的範例，包括使用 DataReader 直接將資料載入物件，以及手動更新沒有資料系結的 UI，請參閱[使用 ADO.NET 建立簡單的資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。

## <a name="object-requirements"></a>物件需求
 自訂物件在 Visual Studio 中使用資料設計工具的唯一需求，就是物件至少需要一個公用屬性。

 一般而言，自訂物件不需要任何特定的介面、函式或屬性做為應用程式的資料來源。 不過，如果您想要將物件從 [**資料來源**] 視窗拖曳至設計介面以建立資料繫結控制項，而且如果物件是執行 <xref:System.ComponentModel.ITypedList> 或 <xref:System.ComponentModel.IListSource> 介面，則物件必須具有預設的函式。 否則，Visual Studio 無法具現化資料來源物件，而且當您將專案拖曳至設計介面時，就會顯示錯誤。

## <a name="examples-of-using-custom-objects-as-data-sources"></a>使用自訂物件做為資料來源的範例
 雖然在使用物件當做資料來源時，有無數的方式可以實作為您的應用程式邏輯，但針對 SQL 資料庫，有幾個標準作業可以使用 Visual Studio 產生的 TableAdapter 物件來簡化。 此頁面說明如何使用 TableAdapters.It 來執行這些標準程式，而不是用來建立自訂物件的指南。 例如，您通常會執行下列標準作業，不論物件的特定執行或應用程式的邏輯為何：

- 將資料載入物件（通常是從資料庫）。

- 建立物件的具類型集合。

- 在集合中加入和移除物件。

- 向使用者顯示表單上的物件資料。

- 變更/編輯物件中的資料。

- 將物件中的資料儲存回資料庫。

> [!NOTE]
> 為了進一步瞭解並提供此頁面上範例的內容，建議您完成下列步驟：[逐步解說：連接至物件中的資料（Windows Forms）](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)。 該逐步解說會建立這裡所討論的物件。

### <a name="loaddata-into-objects"></a>Loaddata 至物件
 在此範例中，您會使用 Tableadapter 將資料載入至物件。 根據預設，會使用兩種方法來建立 Tableadapter，以從資料庫提取資料並填入資料表。

- @No__t_0 方法會將傳回的資料填入現有的資料表。

- @No__t_0 方法會傳回已填入資料的新資料表。

  若要使用資料載入自訂物件，最簡單的方法是呼叫 `TableAdapter.GetData` 方法，在傳回的資料表中，對資料列集合進行迴圈，然後在每個物件中填入每個資料列中的值。 您可以建立 `GetData` 方法，針對加入至 TableAdapter 的任何查詢，傳回已填入的資料表。

> [!NOTE]
> Visual Studio 將 TableAdapter 查詢命名為 `Fill` 並 `GetData` 預設為，但這些名稱可以變更為任何有效的方法名稱。

 下列範例示範如何對資料表中的資料列執行迴圈，並將資料填入物件：

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>建立物件的具類型集合
 您可以為物件建立集合類別，或使用[BindingSource 元件](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)自動提供的具類型集合。

 當您建立物件的自訂集合類別時，建議您從 <xref:System.ComponentModel.BindingList%601> 繼承。 這個泛型類別提供功能來管理您的集合，以及引發事件的能力，將通知傳送至 Windows Forms 中的資料系結基礎結構。

 @No__t_0 中自動產生的集合會針對其具類型的集合使用 <xref:System.ComponentModel.BindingList%601>。 如果您的應用程式不需要額外的功能，您可以在 <xref:System.Windows.Forms.BindingSource> 內維護您的集合。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.BindingSource> 類別的 <xref:System.Windows.Forms.BindingSource.List%2A> 屬性。

> [!NOTE]
> 如果您的集合需要 <xref:System.ComponentModel.BindingList%601> 的基底執行所未提供的功能，您應該建立自訂集合，讓您可以視需要新增至類別。

 下列程式碼示範如何為 `Order` 物件的強型別集合建立類別：

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects 至集合
 您可以藉由呼叫自訂集合類別或 <xref:System.Windows.Forms.BindingSource> 的 `Add` 方法，將物件新增至集合。

 如需使用 <xref:System.Windows.Forms.BindingSource> 將加入至集合的範例，請參閱[逐步解說：連接至物件中的資料（Windows Forms）](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)中的 `LoadCustomers` 方法。

 如需將物件加入至自訂集合的範例，請參閱逐步解說[：連接至物件中的資料（Windows Forms）](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)中的 `LoadOrders` 方法。

> [!NOTE]
> 當您從 <xref:System.ComponentModel.BindingList%601> 繼承時，會自動為您的自訂集合提供 `Add` 方法。

 下列程式碼示範如何在 <xref:System.Windows.Forms.BindingSource> 中將物件加入至具類型的集合：

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 下列程式碼示範如何將物件新增至繼承自 <xref:System.ComponentModel.BindingList%601> 的類型集合：

> [!NOTE]
> 在此範例中，`Orders` 集合是 `Customer` 物件的屬性。

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>從集合中 Removeobjects
 您可以藉由呼叫自訂集合類別或 <xref:System.Windows.Forms.BindingSource> 的 `Remove` 或 `RemoveAt` 方法，從集合中移除物件。

> [!NOTE]
> 當您從 <xref:System.ComponentModel.BindingList%601> 繼承時，系統會自動為您的自訂集合提供 `Remove` 和 `RemoveAt` 方法。

 下列程式碼示範如何使用 <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> 方法，在 <xref:System.Windows.Forms.BindingSource> 中尋找和移除具類型集合中的物件：

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Displayobject 資料給使用者
 若要向使用者顯示物件中的資料，請使用**資料來源**設定 wizard 建立物件資料來源，然後從 [**資料來源**] 視窗將整個物件或個別屬性拖曳至表單上。

### <a name="modify-the-data-in-objects"></a>修改物件中的資料
 若要在系結至 Windows Forms 控制項之資料系結的自訂物件中編輯資料，只需編輯繫結控制項中的資料（或直接在物件的屬性中）。 資料系結架構會更新物件中的資料。

 如果您的應用程式需要追蹤變更，並將建議的變更回復至其原始值，則您必須在物件模型中執行這項功能。 如需資料表如何追蹤提議變更的範例，請參閱 <xref:System.Data.DataRowState>、<xref:System.Data.DataSet.HasChanges%2A> 和 <xref:System.Data.DataTable.GetChanges%2A>。

### <a name="savedata-in-objects-back-to-the-database"></a>將物件中的 Savedata 回資料庫
 藉由將物件的值傳遞至 TableAdapter 的 DBDirect 方法，將資料儲存回資料庫。

 Visual Studio 會建立可以直接針對資料庫執行的 DBDirect 方法。 這些方法不需要 DataSet 或 DataTable 物件。

|TableAdapter DBDirect 方法|描述|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|將新記錄加入至資料庫，可讓您傳入個別的資料行值做為方法參數。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 Update 方法會採用原始和新的資料行值做為方法參數。 原始的值是用來尋找原始記錄，而新值則是用來更新該記錄。<br /><br /> @No__t_0 方法也用來將資料集的變更重新調整回資料庫，方法是採用 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow>s 做為方法參數的陣列。|
|`TableAdapter.Delete`|根據當做方法參數傳入的原始資料行值，從資料庫中刪除現有的記錄。|

 若要儲存物件集合中的資料，請在物件集合中執行迴圈（例如，使用 next 迴圈）。使用 TableAdapter 的 DBDirect 方法，將每個物件的值傳送至資料庫。

 下列範例示範如何使用 `TableAdapter.Insert` DBDirect 方法，將新的客戶直接加入資料庫中：

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
