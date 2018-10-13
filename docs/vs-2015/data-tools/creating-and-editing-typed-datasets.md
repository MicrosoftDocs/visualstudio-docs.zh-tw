---
title: 建立和編輯具類型資料集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225834"
---
# <a name="creating-and-editing-typed-datasets"></a>建立和編輯具類型資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Dataset 設計工具**是一組視覺化工具，可用來建立及編輯具類型資料集和它們所包含的個別項目。  
  
 **Dataset 設計工具**提供視覺表示法中具類型資料集所包含的物件。 您建立和修改[Tableadapter](../data-tools/tableadapter-overview.md)， [TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)， <xref:System.Data.DataTable>s， <xref:System.Data.DataColumn>s，以及<xref:System.Data.DataRelation>向**Dataset 設計工具**。  
  
 若要開啟  **Dataset 設計工具**，連按兩下中的資料集**方案總管**，或以滑鼠右鍵按一下中的資料集**資料來源**視窗，然後按一下**編輯使用設計工具的資料集**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。 加入新<xref:System.Data.DataSet>項目**加入新項目**對話方塊隨即開啟**Dataset 設計工具**空資料集開始編輯。  
  
> [!NOTE]
>  **Dataset 設計工具**可用來擴充資料集的功能。 按兩下設計介面或以滑鼠右鍵按一下並選擇 **檢視程式碼**建立部分類別檔案，您可以在其中加入至資料集不會變更或刪除設計工具程式碼。 如需有關擴充 TableAdapter 的功能，請參閱[擴充 TableAdapter 的功能](../data-tools/extend-the-functionality-of-a-tableadapter.md)。  
  
 下表列出您可以使用完成的一般工作**Dataset 設計工具**。  
  
|以|請參閱|  
|--------|---------|  
|建立 TableAdapter|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|編輯 TableAdapter|[如何： 編輯 Tableadapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|建立 TableAdapter 查詢|[如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)|  
|編輯 TableAdapter 查詢|[如何：編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)|  
|建立 <xref:System.Data.DataTable>|[如何：建立資料表](../data-tools/how-to-create-data-tables.md)|  
|編輯 <xref:System.Data.DataTable>|[設計 DataTable](../data-tools/designing-datatables.md)|  
|建立 <xref:System.Data.DataColumn>|[如何： 將資料行加入至 DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|建立兩個之間的關聯性<xref:System.Data.DataTable>s|[如何： 以 Dataset 設計工具建立 Datarelation](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|擴充功能的資料集|[如何： 擴充資料集的功能](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|將驗證新增至資料表的<xref:System.Data.DataTable.ColumnChanging>事件|[如何： 在資料行變更期間驗證資料](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|將驗證新增至資料表的<xref:System.Data.DataTable.RowChanging>事件|[如何： 在資料列變更期間驗證資料](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>在設計介面上建立物件  
 您可以新增和編輯組成資料集的個別物件，以建立資料集。 下表提供不同的物件中的說明**資料集**索引標籤上**工具箱**，可以將它們拖曳至設計介面：  
  
|Object|描述|  
|------------|-----------------|  
|TableAdapter|包含資料命令和用來與基礎資料庫進行通訊，並填入資料表的資料連接的集合。 如需詳細資訊，請參閱 < [TableAdapter 概觀](../data-tools/tableadapter-overview.md)並[建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。|  
|查詢|TableAdapter 查詢是執行 SQL 陳述式和預存程序的強型別的方法。 執行 TableAdapter 查詢的資料使用資料填入資料表，或執行其他資料庫工作。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。 拖曳資料表的查詢將查詢加入至該資料表中，而將查詢拖曳至空白的地方**Dataset 設計工具**建立全域的查詢。 如需詳細資訊，請參閱 <<c0> [ 如何： 加入至 TableAdapter 的全域查詢](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)。|  
|<xref:System.Data.DataTable>|表示從資料庫傳回的資料列的記憶體中集合。|  
|關聯性 (<xref:System.Data.DataRelation>)|表示兩個之間的父子式關聯性<xref:System.Data.DataTable>s。 如需詳細資訊，請參閱 < [DataRelation 物件簡介](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)並[逐步解說： 建立資料表之間的關聯性](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)。|  
  
> [!NOTE]
>  **Dataset 設計工具**連接至基礎資料庫的資料集時才會建立，設計工具不會自動偵測到資料庫的後續變更。 若要重新整理現有的.xsd，請重新執行**組態精靈**。 如果資料表關聯已變更，請移除 .xsd 中的資料表，再重新加入相關的資料表。  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] 可讓[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)中的資料<xref:System.Data.DataSet>物件。 如需詳細資訊，請參閱 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 以 Dataset 設計工具建立資料集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [逐步解說： 以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [逐步解說： 以 Dataset 設計工具建立 DataTable](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [逐步解說： 建立資料表之間的關聯性](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)