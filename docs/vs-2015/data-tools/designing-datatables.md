---
title: 設計 Datatable |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vbdata.Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- tables [Visual Studio]
- data [Visual Studio], designing DataTables
- DataTable objects
ms.assetid: 17014125-ab28-45ec-8789-01b6fc9a8e6a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f952fbcf6da0185e4f9c1bd6a76b7d15d7f772a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497800"
---
# <a name="designing-datatables"></a>設計 DataTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供設計階段工具用於建立和編輯資料的資料表 (**DataTable**)。 如需功能的概觀**DataTable** ，請參閱[Datatable](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e)。  
  
 下列主題說明如何建立資料表，請將它們新增至使用具類型資料集**Dataset 設計工具**，以及建立和編輯資料行 (**DataColumn**)，定義它們。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立資料表](../data-tools/how-to-create-data-tables.md)  
 提供的步驟來建立新<xref:System.Data.DataTable>具有**Dataset 設計工具**。  
  
 [如何： 將資料行加入至 DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)  
 提供的步驟來建立新<xref:System.Data.DataColumn>中的現有<xref:System.Data.DataTable>。  
  
 [逐步解說：以 DataSet 設計工具建立 DataTable](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)  
 提供逐步指示，建立<xref:System.Data.DataTable>，並定義<xref:System.Data.DataColumn>s 組成其結構。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataSet>  
 代表資料的記憶體中快取。  
  
 <xref:System.Data.DataTable>  
 表示記憶體中資料的一個資料表。  
  
 <xref:System.Data.DataColumn>  
 表示結構描述中的資料行<xref:System.Data.DataTable>。  
  
 <xref:System.Data.DataRelation>  
 表示兩個之間的父子式關聯性<xref:System.Data.DataTable>物件。  
  
## <a name="related-sections"></a>相關章節  
 [DataTable](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e)  
 描述如何建立和自訂`DataTable`物件。  
  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)  
 提供說明如何建立及編輯 TableAdapters 使用設計階段工具的主題連結。  
  
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)  
 提供主題連結，說明不同的方式來連接到 Visual Studio 中的資料。  
  
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 提供資料集是什麼、 如何建立新的資料集，以及如何建立和編輯個別的物件進行的說明主題的連結。  
  
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)  
 提供說明如何執行查詢和預存程序，並將資料載入資料集的主題連結。  
  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 提供主題連結，說明如何透過資料繫結控制項，顯示 Windows Form 上的資料。  
  
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)  
 提供說明如何使用資料集中的主題連結。  
  
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 提供說明要放置程式碼，以驗證資料的主題連結。  
  
 [儲存資料](../data-tools/saving-data.md)  
 提供說明如何將更新的資料傳送至資料庫應用程式從主題的連結。