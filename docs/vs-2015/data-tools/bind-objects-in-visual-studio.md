---
title: 將物件繫結
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 09afb67f0e9431ca8cd520635f243dca70880f09
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683157"
---
# <a name="bind-objects-in-visual-studio"></a>在 Visual Studio 中的物件繫結
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 會提供設計階段工具，為您的應用程式中的資料來源使用自訂的物件。 當您想要將資料庫中的資料儲存在您繫結至 UI 控制項的物件時，建議的方法是使用 Entity Framework 來產生類別。 DbSet 物件上呼叫 AcceptChanges，實體 Frameworkautogenerates 所有未定案變更追蹤程式碼，這表示，任何會變更為本機物件會自動保存至資料庫。    如需詳細資訊，請參閱 < [Entity Framework 文件](https://ef.readthedocs.org/en/latest/)。

> [!TIP]
> 如果您的應用程式已經根據資料集，只應該被視為這篇文章中的物件繫結的方法。如果您已熟悉的資料集，而且您要處理的資料是表格式和不太複雜或太大，也可以使用這些方法。 如需甚至更簡單的範例，牽涉到將資料載入直接物件使用 DataReader，並以手動方式更新 UI 而不需要資料繫結，請參閱[使用 ADO.NET 建立簡單資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。

## <a name="object-requirements"></a>物件的需求
 若要使用資料設計工具，在 Visual Studio 中的自訂物件的唯一需求是物件，必須至少一個公用屬性。

 一般而言，自訂的物件不需要任何特定介面、 建構函式或做為應用程式的資料來源的屬性。 不過，如果您想要將物件從**資料來源**視窗的設計介面，以建立資料繫結控制項，而且如果物件實作<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>介面，物件必須有預設值建構函式。 否則，Visual Studio 無法具現化的資料來源物件，而且它會顯示錯誤，當您將項目拖曳至設計介面。

## <a name="examples-of-using-custom-objects-as-data-sources"></a>使用自訂物件做為資料來源的範例
 雖然有無數的方式來實作您的應用程式邏輯，做為資料來源處理物件時，sql，資料庫有會是可簡化使用 Visual Studio-產生的 TableAdapter 物件的一些標準作業。 此頁面說明如何實作這些標準處理程序使用 TableAdapters.It 不適合做為指南建立您的自訂物件。 例如，您通常會執行下列標準作業，不論特定實作的物件或應用程式的邏輯：

- 將資料載入物件 （通常是從資料庫中）。

- 建立物件的類型的集合。

- 將物件新增至，並移除集合中的物件。

- 使用者在表單上顯示的物件資料。

- 變更/編輯資料物件中。

- 將資料從物件儲存回資料庫。

> [!NOTE]
> 若要進一步了解，，和提供的範例，此頁面上的內容，我們建議您先完成下列：[逐步解說：連接至資料物件 (Windows Form)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)。 該逐步解說建立此處所討論的物件。

### <a name="loaddata-into-objects"></a>物件的 Loaddata
 例如，您將資料載入您的物件使用 Tableadapter。 根據預設，Tableadapter 會建立具有兩種方法，從資料庫擷取資料並填入資料的資料表。

- `TableAdapter.Fill`方法傳回的資料填入現有的資料表。

- `TableAdapter.GetData`方法會傳回新的資料資料表填入資料。

  載入您的自訂物件的資料最簡單方式是呼叫`TableAdapter.GetData`方法，傳回的資料表中的資料列集合執行迴圈，並將填入每個物件中每個資料列的值。 您可以建立`GetData`傳回填入的資料的資料表加入至 TableAdapter 的任何查詢的方法。

> [!NOTE]
> Visual Studio 命名的 TableAdapter 查詢`Fill`和`GetData`根據預設，但是這些名稱可以變更為任何有效的方法名稱。

 下列範例示範如何在資料的資料表中，資料列執行迴圈，並填入具有資料的物件：

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>建立具型別的物件的集合
 您可以建立集合類別，針對您的物件，或使用自動提供的型別的集合[BindingSource 元件](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)。

 當您建立之物件的自訂集合類別時，我們建議您繼承自<xref:System.ComponentModel.BindingList%601>。 這個泛型類別會提供功能來管理您的集合，以及引發事件會傳送通知給 Windows Form 中的資料繫結基礎結構的能力。

 中的自動產生的集合<xref:System.Windows.Forms.BindingSource>使用<xref:System.ComponentModel.BindingList%601>其類型的集合。 如果您的應用程式不需要額外的功能，則您可以維護您的集合內<xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱 <<c0> <xref:System.Windows.Forms.BindingSource.List%2A> 屬性<xref:System.Windows.Forms.BindingSource>類別。

> [!NOTE]
> 如果您的集合需要的功能不提供的基底實作<xref:System.ComponentModel.BindingList%601>，因此您可以視需要新增至類別，您應該建立自訂的集合。

 下列程式碼示範如何建立強型別集合類別`Order`物件：

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects 集合
 將物件新增至集合的藉由呼叫`Add`方法，或您的自訂集合類別的<xref:System.Windows.Forms.BindingSource>。

 如需將加入至集合，使用的範例<xref:System.Windows.Forms.BindingSource>，請參閱 <<c2> `LoadCustomers` 方法中的[逐步解說：連接至資料物件 (Windows Form)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)。

 如需將物件新增至自訂集合的範例，請參閱`LoadOrders`方法中的[逐步解說：連接至資料物件 (Windows Form)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)。

> [!NOTE]
> `Add`方法會自動提供為您自訂的集合。 當您繼承自<xref:System.ComponentModel.BindingList%601>。

 下列程式碼示範如何將物件加入至具型別集合中<xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 下列程式碼示範如何將物件加入至繼承的型別集合<xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> 在此範例中`Orders`集合是屬性`Customer`物件。

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>從集合 Removeobjects
 從集合移除物件呼叫`Remove`或是`RemoveAt`方法，或您的自訂集合類別的<xref:System.Windows.Forms.BindingSource>。

> [!NOTE]
> `Remove`並`RemoveAt`方法會自動提供給您的自訂集合當您繼承自<xref:System.ComponentModel.BindingList%601>。

 下列程式碼顯示如何尋找及移除的具類型的集合中的物件<xref:System.Windows.Forms.BindingSource>與<xref:System.Windows.Forms.BindingSource.RemoveAt%2A>方法：

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Displayobject 資料給使用者
 若要顯示給使用者的物件資料，建立物件資料來源使用**資料來源組態**精靈，然後將整個物件或個別的屬性拖曳到您的表單，從**Zdroje dat**視窗。

### <a name="modify-the-data-in-objects"></a>修改物件中的資料
 若要編輯資料繫結至 Windows Form 控制項的自訂物件中的資料，只需編輯繫結控制項 （或直接在物件的屬性中） 中的資料。 資料繫結架構更新之物件中的資料。

 如果您的應用程式需要追蹤變更，並建議變更復原為其原始值，您必須在物件模型中實作這項功能。 如需如何資料資料表追蹤的提議的變更的範例，請參閱<xref:System.Data.DataRowState>， <xref:System.Data.DataSet.HasChanges%2A>，和<xref:System.Data.DataTable.GetChanges%2A>。

### <a name="savedata-in-objects-back-to-the-database"></a>回到資料庫的物件中的 Savedata
 您的物件中的值傳遞至 TableAdapter 的 DBDirect 方法，將資料儲存回資料庫。

 Visual Studio 會建立可直接對資料庫執行的 DBDirect 方法。 這些方法不需要 DataSet 或 DataTable 物件。

|TableAdapter DBDirect 方法|描述|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|將新的記錄加入至資料庫，可讓您在個別的資料行值做為方法參數傳遞。|
|`TableAdapter.Update`|更新現有的資料庫中的記錄。 更新方法會接受原始及新的資料行值作為方法參數。 原始的值用來找出原始記錄中，與新的值來更新該記錄。<br /><br /> `TableAdapter.Update`方法也會用來協調回資料庫，資料集內的變更，藉由採取<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或陣列<xref:System.Data.DataRow>做為方法參數。|
|`TableAdapter.Delete`|刪除現有記錄從資料庫根據原始的資料行值傳遞為方法參數。|

 若要用於儲存的資料物件的集合，循環的 （例如，使用的下一個迴圈） 的物件集合。使用 TableAdapter 的 DBDirect 方法，每個物件的值傳送至資料庫。

 下列範例示範如何使用`TableAdapter.Insert`DBDirect 方法來加入新的客戶，直接在資料庫：

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>另請參閱
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
