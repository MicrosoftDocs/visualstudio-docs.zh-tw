---
title: 如何： 更新資料庫中的記錄 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b880353b227eae86c7c35f274271fb404b62ede0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199510"
---
# <a name="how-to-update-records-in-a-database"></a>如何：更新資料庫中的資料錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用`TableAdapter.Update`方法，以在資料庫中的更新 （編輯） 記錄。 `TableAdapter.Update`方法提供數個多載執行傳入的參數而定的不同作業。 請務必了解呼叫這些不同的方法簽章的結果。  
  
> [!NOTE]
>  如果您的應用程式不會使用 TableAdapters，則您可以使用命令物件來更新您的資料庫中的記錄 (例如<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>)。 如需有關命令物件以更新資料的詳細資訊，請參閱下方的 「 使用命令物件的更新記錄 」。  
  
 下表描述的各種行為`TableAdapter.Update`方法：  
  
|方法|描述|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|嘗試儲存中的所有變更<xref:System.Data.DataTable>到資料庫。 （這包括移除任何刪除從資料表中，加入資料列插入至資料表，以及更新資料表中已經變更的任何資料列的資料列）。|  
|`TableAdapter.Update(DataSet)`|雖然此參數只接受資料集，TableAdapter 嘗試在 TableAdapter 中儲存所有變更的相關聯<xref:System.Data.DataTable>到資料庫。 （這包括移除任何刪除從資料表中，新增資料列在資料表中，插入和更新資料表中已經變更的任何資料列的資料列）。**注意︰** TableAdapter 的相關聯<xref:System.Data.DataTable>是<xref:System.Data.DataTable>TableAdapter 原先設定時所建立。|  
|`TableAdapter.Update(DataRow)`|嘗試將變更儲存在指定<xref:System.Data.DataRow>到資料庫。|  
|`TableAdapter.Update(DataRows())`|嘗試將變更儲存在陣列中的任何資料列<xref:System.Data.DataRow>的資料庫。|  
|`TableAdapter.Update("new column values", "original column values")`|嘗試將變更儲存在原始的資料行值所識別的單一資料列。|  
  
 您通常會使用`TableAdapter.Update`方法採用<xref:System.Data.DataSet>， <xref:System.Data.DataTable>，或<xref:System.Data.DataRow>(s) (當您的應用程式使用資料集以獨佔方式來儲存資料。  
  
 您通常會使用`TableAdapter.Update`取得資料行值，當您的應用程式使用物件來儲存資料的方法。  
  
 如果沒有您 TableAdapter`Update`則表示可能是 TableAdapter 已設定為使用預存程序會採用資料行值的方法或其`GenerateDBDirectMethods`屬性設定為`false`。 嘗試設定 TableAdapter`GenerateDBDirectMethods`屬性，以`true`內在[Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)，然後將儲存的資料集，以重新產生的 TableAdapter。 如果 TableAdapter 仍沒有`Update`方法採用資料行值，則資料表可能未提供足夠的結構描述資訊來區分個別資料列 （例如，資料表上設定沒有主索引鍵）。  
  
## <a name="update-existing-records-using-tableadapters"></a>更新現有的記錄，使用 Tableadapter  
 Tableadapter 會提供不同的方式，來更新資料庫，以根據您的應用程式的需求中的記錄。  
  
 如果您的應用程式使用資料集來儲存資料，則您只要更新中所需的資料錄<xref:System.Data.DataTable>，然後呼叫`TableAdapter.Update`方法並傳入<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或陣列<xref:System.Data.DataRow>s。 上表描述不同`Update`方法。  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>若要更新資料庫中的記錄與使用 DataSet、 DataTable、 DataRow，或是 DataRows() TableAdapter.Update 方法  
  
1.  編輯所需的資料錄<xref:System.Data.DataTable>藉由直接編輯<xref:System.Data.DataRow>在<xref:System.Data.DataTable>。 如需詳細資訊，請參閱 <<c0> [ 如何： 編輯 DataTable 中的資料列](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c)。  
  
2.  在 編輯資料列之後<xref:System.Data.DataTable>，呼叫`TableAdapter.Update`方法。 您可以控制要藉由傳入整個更新的資料量<xref:System.Data.DataSet>，則<xref:System.Data.DataTable>，陣列<xref:System.Data.DataRow>或單一<xref:System.Data.DataRow>。  
  
     下列程式碼示範如何編輯中的資料錄<xref:System.Data.DataTable>，然後呼叫`TableAdapter.Update`方法，以將變更儲存到資料庫。 （此範例使用 Northwind 資料庫區域資料表）。  
  
     [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
     [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
 如果您的應用程式會使用物件來將資料儲存在您的應用程式，您可以使用 TableAdapter 的`DBDirect`將資料從您的物件傳送到資料庫的直接方法。 這些方法可讓您將每個資料行的個別值傳遞為方法參數。 呼叫這個方法會傳遞至方法的資料行值更新資料庫中的現有記錄。  
  
 下列程序會使用 Northwind`Region`做為範例的資料表。  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>若要更新記錄在資料庫中使用 取得資料行值 TableAdapter.Update 方法  
  
-   呼叫 TableAdapter 的`Update`方法並傳入新值和原始值的每個資料行做為參數。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>使用命令物件的更新記錄  
 下列範例會更新現有的記錄，直接在資料庫中使用命令物件。 如需有關如何使用命令物件來執行命令和預存程序的詳細資訊，請參閱 <<c0> [ 將資料提取到您的應用程式](../data-tools/fetching-data-into-your-application.md)。  
  
 下列程序會使用 Northwind`Region`做為範例的資料表。  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>若要更新現有的記錄，在資料庫中使用命令物件  
  
-   建立新的命令物件;設定其`Connection`， `CommandType`，和`CommandText`[屬性]，然後開啟的連接，然後執行命令。  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必須存取您嘗試連接的資料庫，以及更新所需的資料表中記錄的權限。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何： 刪除資料庫中的記錄](../data-tools/how-to-delete-records-in-a-database.md)   
 [將新記錄插入資料庫](../data-tools/insert-new-records-into-a-database.md)   
 [將資料儲存至資料庫物件](../data-tools/save-data-from-an-object-to-a-database.md)   
 [在 Visual Studio 中的資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)