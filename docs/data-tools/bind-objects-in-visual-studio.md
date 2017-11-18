---
title: "在 Visual Studio 中的物件繫結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9f410fdfea8a241b10cbab621dbd781d3648a080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bind-objects-in-visual-studio"></a>在 Visual Studio 中的物件繫結
Visual Studio 會提供設計階段工具，為您的應用程式中的資料來源使用自訂物件。 當您想要將資料庫的資料儲存在您繫結至 UI 控制項的物件時，建議的方法就是使用 Entity Framework 來產生類別。 Entity Framework 自動產生所有重複使用變更追蹤程式碼，這表示，本機物件的任何變更會自動保存至資料庫時您 DbSet 物件上呼叫 AcceptChanges。 如需詳細資訊，請參閱[Entity Framework 文件](https://ef.readthedocs.org/en/latest/)。  
  
> [!TIP]
>  如果您的應用程式已經根據資料集，應該只考慮這篇文章中的物件繫結的方法。如果您已熟悉的資料集，而且您要處理的資料是表格式和太複雜或太大，也可以使用這些方法。 如需甚至更簡單的範例，牽涉到將資料載入直接物件藉由使用 DataReader 手動更新 UI 而不進行資料繫結，請參閱[使用 ADO.NET 建立簡單資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。  
  
## <a name="object-requirements"></a>物件的需求  
 若要使用資料設計工具，Visual Studio 中的自訂物件的唯一需求是需要至少一個公用屬性，該物件。  
  
 一般而言，自訂物件不需要任何特定介面、 建構函式或做為應用程式的資料來源的屬性。 不過，如果您想要將物件從**資料來源**視窗至設計介面，以建立資料繫結控制項，而且如果物件實作<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>介面，物件必須有預設值建構函式。 否則，Visual Studio 無法具現化的資料來源物件，而且它會顯示錯誤，當您將項目拖曳至設計介面。  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>使用自訂物件做為資料來源的範例  
 有無數的方式來實作您的應用程式邏輯，做為資料來源使用物件時，sql database 有。 一些標準的作業，可簡化使用 Visual Studio 產生的 TableAdapter 物件 此頁面說明如何實作這些標準處理程序使用 TableAdapters.It 不適合做為指南建立自訂物件。 例如，您通常會執行下列標準作業，不論特定實作的物件或應用程式的邏輯：  
  
-   將資料載入物件 （通常是從資料庫中）。  
  
-   建立具類型的物件集合。  
  
-   將物件新增至，並從集合中移除物件。  
  
-   顯示在表單上的使用者物件資料。  
  
-   變更/編輯的資料物件中。  
  
-   將資料從物件儲存回資料庫。   
  
### <a name="load-data-into-objects"></a>將資料載入物件  
 例如，您將資料載入物件使用 Tableadapter。 根據預設，Tableadapter 會建立具有兩種方法，從資料庫擷取資料並填入資料的資料表。  
  
-   `TableAdapter.Fill`方法傳回的資料填入現有資料表。  
  
-   `TableAdapter.GetData`方法會傳回新的資料表會填入資料。  
  
 載入自訂資料物件的最簡單方式是呼叫`TableAdapter.GetData`方法，傳回的資料表中的資料列集合執行迴圈，並將填入每個物件中每個資料列的值。 您可以建立`GetData`傳回已填入的資料的資料表加入至 TableAdapter 的任何查詢的方法。  
  
> [!NOTE]
>  Visual Studio 命名 TableAdapter 查詢`Fill`和`GetData`根據預設，但是可以變更這些名稱的任何有效的方法名稱。  
  
 下列範例會示範如何重複使用的資料表資料列資料，並填入具有資料的物件：  
  
 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### <a name="create-a-typed-collection-of-objects"></a>建立物件的集合型別  
 您可以建立的集合類別的物件，或使用由自動提供的類型的集合[BindingSource 元件](/dotnet/framework/winforms/controls/bindingsource-component)。  
  
 當您建立之物件的自訂集合類別時，我們建議您繼承自<xref:System.ComponentModel.BindingList%601>。 此泛型類別提供功能來管理您的集合，以及引發事件會傳送通知給 Windows Form 中的資料繫結基礎結構的能力。  
  
 中的自動產生集合<xref:System.Windows.Forms.BindingSource>使用<xref:System.ComponentModel.BindingList%601>其類型的集合。 如果您的應用程式不需要額外的功能，則您可以維護您的集合內<xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱<xref:System.Windows.Forms.BindingSource.List%2A>屬性<xref:System.Windows.Forms.BindingSource>類別。  
  
> [!NOTE]
>  如果您的集合需要的功能未提供的基底實作<xref:System.ComponentModel.BindingList%601>，因此您可以依需要新增至類別，您應該建立自訂的集合。  
  
 下列程式碼示範如何建立強型別集合的類別`Order`物件：  
  
 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### <a name="add-objects-to-a-collection"></a>將物件加入至集合  
 將物件加入至集合的呼叫`Add`方法，或您的自訂集合類別的<xref:System.Windows.Forms.BindingSource>。  
  
 
> [!NOTE]
>  `Add`方法會自動提供給您自訂的集合。 當您繼承自<xref:System.ComponentModel.BindingList%601>。  
  
 下列程式碼示範如何將物件加入至具型別集合中<xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 下列程式碼示範如何將物件加入至繼承的型別集合<xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  在此範例中`Orders`集合是屬性的`Customer`物件。  
  
 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### <a name="remove-objects-from-a-collection"></a>從集合中移除物件  
 從集合移除物件藉由呼叫`Remove`或`RemoveAt`方法，或您的自訂集合類別的<xref:System.Windows.Forms.BindingSource>。  
  
> [!NOTE]
>  `Remove`和`RemoveAt`方法會自動提供為您自訂的集合。 當您繼承自<xref:System.ComponentModel.BindingList%601>。  
  
 下列程式碼示範如何找出並從具型別集合中移除物件<xref:System.Windows.Forms.BindingSource>與<xref:System.Windows.Forms.BindingSource.RemoveAt%2A>方法：  
  
 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### <a name="display-object-data-to-users"></a>向使用者顯示物件資料  
 若要顯示給使用者物件資料，建立物件資料來源使用**資料來源組態**精靈，然後將整個物件或個別屬性拖曳至表單，從**資料來源**視窗。  
  
### <a name="modify-the-data-in-objects"></a>修改物件中的資料  
 若要編輯的資料繫結至 Windows Form 控制項的自訂物件中的資料，只需編輯繫結控制項 （或直接在物件內容中） 中的資料。 資料繫結架構更新物件中的資料。  
  
 如果您的應用程式需要追蹤變更，並建議變更復原為其原始值，您必須在物件模型中實作這項功能。 如需如何資料資料表追蹤的建議的變更的範例，請參閱<xref:System.Data.DataRowState>， <xref:System.Data.DataSet.HasChanges%2A>，和<xref:System.Data.DataTable.GetChanges%2A>。  
  
### <a name="save-data-in-objects-back-to-the-database"></a>將資料儲存在資料庫物件  
 從物件的值傳遞至 TableAdapter 的 DBDirect 方法，將資料儲存回資料庫。  
  
 Visual Studio 會建立可以直接對資料庫執行的 DBDirect 方法。 這些方法不需要 DataSet 或 DataTable 物件。  
  
|TableAdapter DBDirect 方法|說明|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|將新記錄新增至資料庫，讓您在個別資料行值做為方法參數中傳遞。|  
|`TableAdapter.Update`|更新現有的資料庫中的記錄。 更新方法會接受原始和新的資料行值做為方法參數。 用來尋找原始記錄中，原始值和新值來更新該記錄。<br /><br /> `TableAdapter.Update`方法也用來協調回資料庫，變更集中的資料，採取<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或陣列<xref:System.Data.DataRow>做為方法參數。|  
|`TableAdapter.Delete`|刪除現有記錄為方法參數傳入的原始資料行值為基礎的資料庫。|  
  
 若要將資料儲存從物件的集合，循環 （例如，使用迴圈的下一步） 物件的集合。使用 TableAdapter 的 DBDirect 方法，每個物件的值傳送至資料庫。  
  
 下列範例示範如何使用`TableAdapter.Insert`DBDirect 方法，將新的客戶，直接在資料庫：  
  
 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)