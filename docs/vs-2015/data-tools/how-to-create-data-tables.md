---
title: 如何： 建立資料的資料表 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497167"
---
# <a name="how-to-create-data-tables"></a>如何：建立資料表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

資料可以儲存在記憶體中<xref:System.Data.DataTable>物件。 (資料集組成<xref:System.Data.DataTable>物件。)您通常會使用 Tableadapter 建立新的資料表[TableAdapter 組態精靈](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)或從資料庫物件拖曳**伺服器總管**拖曳至**Dataset 設計工具**.  
  
 當您建立新的 Tableadapter 中資料的資料表建立副產品[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)，但它們也可以建立獨立。 您將建立的獨立資料表格<xref:System.Data.DataTable>物件從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。  
  
> [!NOTE]
>  若要以程式設計方式建立資料的資料表，請參閱[建立 DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>建立 tableadapter 的 DataTable  
 使用 Tableadapter 的資料表包括資料表中填入資料，並將變更寫回資料庫的方法。 執行建立 TableAdapters **TableAdapter 組態精靈**或從資料庫物件拖曳**伺服器總管**拖曳至**Dataset 設計工具**。  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>使用 TableAdapter 建立新的資料表  
  
1.  開啟您的資料集，在**Dataset 設計工具**。 如需資訊，請參閱[如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  拖曳**TableAdapter**從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。  
  
     **TableAdapter 組態精靈**隨即開啟。  
  
3.  完成精靈。 如需詳細資訊，請參閱[TableAdapter 組態精靈](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>若要從伺服器總管以 tableadapter 建立新的資料表  
  
1.  開啟您的資料集，在**資料來源設計師**。  
  
2.  從資料庫物件 （例如資料表） 拖曳**伺服器總管**拖曳至**Dataset 設計工具**。  
  
## <a name="creating-a-standalone-datatable"></a>建立獨立 DataTable  
 獨立資料表必須先`Fill`實作邏輯，以填滿資料。 如需有關填滿獨立資料資料表，請參閱[從 DataAdapter 填入 DataSet](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)。  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>若要建立新的獨立資料資料表  
  
1.  開啟您的資料集，在**Dataset 設計工具**。  
  
2.  拖曳<xref:System.Data.DataTable>從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。  
  
3.  新增資料行來定義您的資料表。 如需詳細資訊，請參閱 <<c0> [ 如何： 將資料行新增至 DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataTable>   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)