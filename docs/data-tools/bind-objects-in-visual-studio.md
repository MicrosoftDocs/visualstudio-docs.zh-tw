---
title: 資料系結自訂物件
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b9994d52c5ca39d744cf26dc019440e70e809ee8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925667"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>在 Visual Studio 中將物件系結為數據源

Visual Studio 提供設計階段工具, 可讓您在應用程式中使用自訂物件做為資料來源。 當您想要將資料庫中的資料儲存在您系結至 UI 控制項的物件中時, 建議的方法是使用 Entity Framework 來產生類別或類別。 Entity Framework 會自動產生所有的未定案變更追蹤程式碼, 這表示當您在 DbSet 物件上呼叫 AcceptChanges 時, 對本機物件所做的任何變更都會自動儲存到資料庫。 如需詳細資訊, 請參閱[Entity Framework 檔](https://ef.readthedocs.org/en/latest/)。

> [!TIP]
> 只有在您的應用程式已根據資料集時, 才應該考慮本文中的物件系結方法。 如果您已經熟悉資料集, 也可以使用這些方法, 而您要處理的資料是表格式, 而且不太複雜或太大。 如需更簡單的範例, 包括使用 DataReader 直接將資料載入物件, 以及手動更新沒有資料系結的 UI, 請參閱[使用 ADO.NET 建立簡單的資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。

## <a name="object-requirements"></a>物件需求

自訂物件在 Visual Studio 中使用資料設計工具的唯一需求, 就是物件至少需要一個公用屬性。

一般而言, 自訂物件不需要任何特定的介面、函式或屬性做為應用程式的資料來源。 不過, 如果您想要將物件從 [**資料來源**] 視窗拖曳至設計介面以建立資料繫結控制項, 而且如果物件<xref:System.ComponentModel.ITypedList>是執行或<xref:System.ComponentModel.IListSource>介面, 則物件必須具有預設的函式。 否則, Visual Studio 無法具現化資料來源物件, 而且當您將專案拖曳至設計介面時, 就會顯示錯誤。

## <a name="examples-of-using-custom-objects-as-data-sources"></a>使用自訂物件做為資料來源的範例

雖然在使用物件當做資料來源時, 有無數的方式可以實作為您的應用程式邏輯, 但針對 SQL 資料庫, 有幾個標準作業可以使用 Visual Studio 產生的 TableAdapter 物件來簡化。 此頁面說明如何使用 Tableadapter 來執行這些標準處理常式。 其目的不是建立自訂物件的指南。 例如, 您通常會執行下列標準作業, 不論物件的特定執行或應用程式的邏輯為何:

- 將資料載入物件 (通常是從資料庫)。

- 建立物件的具類型集合。

- 在集合中加入和移除物件。

- 向使用者顯示表單上的物件資料。

- 變更/編輯物件中的資料。

- 將物件中的資料儲存回資料庫。

### <a name="load-data-into-objects"></a>將資料載入物件

在此範例中, 您會使用 Tableadapter 將資料載入至物件。 根據預設, 會使用兩種方法來建立 Tableadapter, 以從資料庫提取資料並填入資料表。

- `TableAdapter.Fill`方法會將傳回的資料填入現有的資料表。

- `TableAdapter.GetData`方法會傳回已填入資料的新資料表。

若要以資料載入自訂物件, 最簡單的方法是`TableAdapter.GetData`呼叫方法, 並在傳回的資料表中, 對資料列集合進行迴圈, 然後在每個物件中填入每個資料列中的值。 您可以建立`GetData`方法, 針對加入 TableAdapter 的任何查詢, 傳回已填入的資料表。

> [!NOTE]
> Visual Studio 將 TableAdapter 查詢`Fill` `GetData`命名為, 但根據預設, 您可以將這些名稱變更為任何有效的方法名稱。

下列範例示範如何對資料表中的資料列執行迴圈, 並將資料填入物件:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>建立物件的具類型集合

您可以為物件建立集合類別, 或使用[BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)自動提供的具類型集合。

當您要建立物件的自訂集合類別時, 建議您從<xref:System.ComponentModel.BindingList%601>繼承。 這個泛型類別提供功能來管理您的集合, 以及引發事件的能力, 將通知傳送至 Windows Forms 中的資料系結基礎結構。

在中<xref:System.Windows.Forms.BindingSource>自動產生的集合會<xref:System.ComponentModel.BindingList%601>針對其具類型的集合使用。 如果您的應用程式不需要額外的功能, 您可以在中維護<xref:System.Windows.Forms.BindingSource>您的集合。 如需詳細資訊, 請<xref:System.Windows.Forms.BindingSource.List%2A>參閱<xref:System.Windows.Forms.BindingSource>類別的屬性。

> [!NOTE]
> 如果您的集合所需的功能不是由的基<xref:System.ComponentModel.BindingList%601>底實作為提供, 您應該建立自訂集合, 讓您可以視需要新增至類別。

下列程式碼示範如何為`Order`物件的強型別集合建立類別:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>將物件新增至集合

您可以藉由呼叫`Add`自訂集合類別或<xref:System.Windows.Forms.BindingSource>的方法, 將物件加入至集合。

> [!NOTE]
> 當您從<xref:System.ComponentModel.BindingList%601>繼承時, 會自動提供自訂集合的方法。`Add`

下列程式碼示範如何在中<xref:System.Windows.Forms.BindingSource>將物件加入至具類型的集合:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

下列程式碼示範如何將物件加入至繼承自<xref:System.ComponentModel.BindingList%601>的具類型集合:

> [!NOTE]
> 在此範例中, `Orders`集合是`Customer`物件的屬性。

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>從集合中移除物件

您可以藉由呼叫`Remove`自訂集合類別或的<xref:System.Windows.Forms.BindingSource>或`RemoveAt`方法, 從集合中移除物件。

> [!NOTE]
> 當`Remove`您`RemoveAt` 從<xref:System.ComponentModel.BindingList%601>繼承時, 會自動為您的自訂集合提供和方法。

下列程式碼示範如何<xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>使用方法, 在中從具類型的集合中找出並移除物件:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>向使用者顯示物件資料

若要向使用者顯示物件中的資料, 請使用**資料來源**設定 wizard 建立物件資料來源, 然後從 [**資料來源**] 視窗將整個物件或個別屬性拖曳至表單上。

### <a name="modify-the-data-in-objects"></a>修改物件中的資料

若要在系結至 Windows Forms 控制項之資料系結的自訂物件中編輯資料, 只需編輯繫結控制項中的資料 (或直接在物件的屬性中)。 資料系結架構會更新物件中的資料。

如果您的應用程式需要追蹤變更, 並將建議的變更回復至其原始值, 則您必須在物件模型中執行這項功能。 如需資料表如何追蹤建議變更的範例, 請參閱<xref:System.Data.DataRowState>、 <xref:System.Data.DataSet.HasChanges%2A>和<xref:System.Data.DataTable.GetChanges%2A>。

### <a name="save-data-in-objects-back-to-the-database"></a>將物件中的資料儲存回資料庫

藉由將物件的值傳遞至 TableAdapter 的 DBDirect 方法, 將資料儲存回資料庫。

Visual Studio 會建立可以直接針對資料庫執行的 DBDirect 方法。 這些方法不需要 DataSet 或 DataTable 物件。

|TableAdapter DBDirect 方法|說明|
| - |-----------------|
|`TableAdapter.Insert`|將新記錄加入至資料庫, 可讓您傳入個別的資料行值做為方法參數。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 Update 方法會採用原始和新的資料行值做為方法參數。 原始的值是用來尋找原始記錄, 而新值則是用來更新該記錄。<br /><br /> 方法`TableAdapter.Update`也會使用的<xref:System.Data.DataSet>、 <xref:System.Data.DataTable> <xref:System.Data.DataRow>、或的<xref:System.Data.DataRow>陣列做為方法參數, 藉此將 dataset 中的變更重新協調回資料庫。|
|`TableAdapter.Delete`|根據當做方法參數傳入的原始資料行值, 從資料庫中刪除現有的記錄。|

若要儲存物件集合中的資料, 請在物件集合中執行迴圈 (例如, 使用 next 迴圈)。 使用 TableAdapter 的 DBDirect 方法, 將每個物件的值傳送至資料庫。

下列範例示範如何使用`TableAdapter.Insert` DBDirect 方法, 將新的客戶直接加入資料庫中:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)