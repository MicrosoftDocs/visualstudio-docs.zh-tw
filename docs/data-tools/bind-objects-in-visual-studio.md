---
title: 資料系結自訂物件
description: 將物件系結為 Visual Studio 中的資料來源。 使用設計階段工具，將自訂物件做為應用程式中的資料來源使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 140700615759404f02109c4506f4c27d083a74b1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215535"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>將物件系結為 Visual Studio 中的資料來源

Visual Studio 提供可在應用程式中使用自訂物件作為資料來源的設計階段工具。 當您想要將資料庫中的資料儲存在系結至 UI 控制項的物件中時，建議的方法是使用 Entity Framework 產生類別或類別。 Entity Framework 自動產生所有未定案的變更追蹤程式碼，這表示當您在 DbSet 物件上呼叫 AcceptChanges 時，對本機物件所做的任何變更都會自動儲存到資料庫。 如需詳細資訊，請參閱 [Entity Framework 檔](https://ef.readthedocs.org/en/latest/)。

> [!TIP]
> 只有當您的應用程式已經以資料集為基礎時，才應該考慮本文中的物件系結方法。 如果您已經熟悉資料集，您也可以使用這些方法，而您要處理的資料是表格式的，且不太複雜或太大。 如需更簡單的範例，包括使用 DataReader 直接將資料載入物件，以及手動更新沒有資料系結的 UI，請參閱 [使用 ADO.NET 建立簡單的資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。

## <a name="object-requirements"></a>物件需求

自訂物件在 Visual Studio 中使用資料設計工具的唯一需求是，物件需要至少一個公用屬性。

一般而言，自訂物件不需要任何特定的介面、函式或屬性作為應用程式的資料來源。 但是，如果您想要將物件從 [ **資料來源** ] 視窗拖曳至設計介面以建立資料繫結控制項，而且如果物件是執行 <xref:System.ComponentModel.ITypedList> 或 <xref:System.ComponentModel.IListSource> 介面，則物件必須有預設的函式。 否則，Visual Studio 無法將資料來源物件具現化，當您將專案拖曳至設計介面時，就會顯示錯誤。

## <a name="examples-of-using-custom-objects-as-data-sources"></a>使用自訂物件作為資料來源的範例

當您使用物件作為資料來源時，有無數種方式可以實作為應用程式邏輯，而針對 SQL database，則有一些標準作業可以使用 Visual Studio 產生的 TableAdapter 物件來簡化。 此頁面說明如何使用 Tableadapter 來執行這些標準進程。 它不是用來建立自訂物件的指南。 例如，您通常會執行下列標準作業，不論物件的特定執行或應用程式的邏輯為何：

- 將資料載入至物件 (通常是從資料庫) 。

- 建立物件的具類型集合。

- 在集合中加入和移除物件。

- 將物件資料顯示到表單上的使用者。

- 變更/編輯物件中的資料。

- 將物件的資料儲存回資料庫。

### <a name="load-data-into-objects"></a>將資料載入物件中

在此範例中，您會使用 Tableadapter 將資料載入至物件。 根據預設，會使用兩種方法來建立 Tableadapter，以從資料庫提取資料並填入資料表。

- 方法會將 `TableAdapter.Fill` 傳回的資料填入現有的資料表。

- 方法會傳回 `TableAdapter.GetData` 填入資料的新資料表。

若要使用資料載入自訂物件，最簡單的方式就是呼叫 `TableAdapter.GetData` 方法、在傳回之資料表的資料列集合中執行迴圈，然後以每個資料列中的值填入每個物件。 您可以建立 `GetData` 方法，以針對任何已加入至 TableAdapter 的查詢傳回填入的資料表。

> [!NOTE]
> Visual Studio 將 TableAdapter 查詢命名 `Fill` `GetData` 為預設值，但您可以將這些名稱變更為任何有效的方法名稱。

下列範例顯示如何在資料表的資料列中執行迴圈，並以資料填入物件：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>建立物件的具類型集合

您可以建立物件的集合類別，或使用 [BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)自動提供的型別集合。

當您要建立物件的自訂集合類別時，建議您從繼承 <xref:System.ComponentModel.BindingList%601> 。 這個泛型類別提供管理集合的功能，以及在 Windows Forms 中引發傳送通知至資料系結基礎結構之事件的能力。

在中自動產生的集合會 <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> 針對其具類型的集合使用。 如果您的應用程式不需要額外的功能，您可以在中維護您的集合 <xref:System.Windows.Forms.BindingSource> 。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.BindingSource.List%2A> 類別的屬性 <xref:System.Windows.Forms.BindingSource> 。

> [!NOTE]
> 如果您的集合需要的基底執行未提供的功能 <xref:System.ComponentModel.BindingList%601> ，您應該建立自訂集合，以便您可以視需要新增至類別。

下列程式碼將示範如何建立物件之強型別集合的類別 `Order` ：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>將物件加入至集合

您可以藉由呼叫 `Add` 自訂集合類別或的方法，將物件加入至集合 <xref:System.Windows.Forms.BindingSource> 。

> [!NOTE]
> `Add`當您繼承自時，會自動為您的自訂集合提供方法 <xref:System.ComponentModel.BindingList%601> 。

下列程式碼示範如何將物件加入至中的具類型集合 <xref:System.Windows.Forms.BindingSource> ：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

下列程式碼示範如何將物件加入至繼承自的類型集合 <xref:System.ComponentModel.BindingList%601> ：

> [!NOTE]
> 在此範例中， `Orders` 集合是物件的屬性 `Customer` 。

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>從集合中移除物件

您可以藉由呼叫 `Remove` `RemoveAt` 自訂集合類別或的方法，從集合移除物件 <xref:System.Windows.Forms.BindingSource> 。

> [!NOTE]
> `Remove` `RemoveAt` 當您繼承自時，會自動為您的自訂集合提供和方法 <xref:System.ComponentModel.BindingList%601> 。

下列程式碼示範如何使用方法，在中從具類型的集合尋找和移除物件 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> ：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>向使用者顯示物件資料

若要向使用者顯示物件中的資料，請使用 [ **資料來源** 設定] wizard 建立物件資料來源，然後從 [ **資料來源** ] 視窗將整個物件或個別屬性拖曳至表單。

### <a name="modify-the-data-in-objects"></a>修改物件中的資料

若要在資料系結至 Windows Forms 控制項的自訂物件中編輯資料，只要在繫結控制項中編輯資料 (或直接在物件的屬性) 中編輯。 資料系結架構會更新物件中的資料。

如果您的應用程式需要追蹤變更，以及回復其原始值的建議變更，則您必須在物件模型中執行這項功能。 如需資料表如何追蹤建議的變更的範例，請參閱 <xref:System.Data.DataRowState> 、 <xref:System.Data.DataSet.HasChanges%2A> 和 <xref:System.Data.DataTable.GetChanges%2A> 。

### <a name="save-data-in-objects-back-to-the-database"></a>將物件中的資料儲存回資料庫

藉由將物件中的值傳遞給 TableAdapter 的 DBDirect 方法，將資料儲存回資料庫。

Visual Studio 會建立可以直接對資料庫執行的 DBDirect 方法。 這些方法不需要 DataSet 或 DataTable 物件。

|TableAdapter DBDirect 方法|描述|
| - |-----------------|
|`TableAdapter.Insert`|將新的記錄加入至資料庫，讓您以方法參數的形式傳入個別的資料行值。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 Update 方法會採用原始和新的資料行值做為方法參數。 原始值會用來尋找原始記錄，而新的值會用來更新該記錄。<br /><br /> `TableAdapter.Update`方法也可用來將 <xref:System.Data.DataSet> 、 <xref:System.Data.DataTable> 、 <xref:System.Data.DataRow> 或的陣列 <xref:System.Data.DataRow> 視為方法參數，以將資料集的變更重新協調回資料庫。|
|`TableAdapter.Delete`|根據傳入做為方法參數的原始資料行值，從資料庫中刪除現有的記錄。|

若要從物件的集合儲存資料，請在物件集合中迴圈 (例如，使用 for next 迴圈) 。 使用 TableAdapter 的 DBDirect 方法，將每個物件的值傳送至資料庫。

下列範例示範如何使用 `TableAdapter.Insert` DBDirect 方法，將新的客戶直接新增至資料庫中：

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>另請參閱

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
