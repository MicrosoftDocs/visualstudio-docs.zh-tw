---
title: 如何： 編輯 TableAdapter 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 687336b979ef7e6d46ea6deb4a5682f3aec065be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287894"
---
# <a name="how-to-edit-tableadapter-queries"></a>如何：編輯 TableAdapter 查詢
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯 TableAdapter 查詢[編輯 TableAdapters](../data-tools/editing-tableadapters.md)中**Dataset 設計工具**。 當它不再符合您的應用程式的需求時，您應該修改 TableAdapter 查詢。 （或者，您可以建立其他查詢的 TableAdapter 上。 如需有關加入新的查詢的詳細資訊，請參閱[如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。)  
  
> [!NOTE]
>  如果[TableAdapter 組態精靈](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)隨即開啟，而不是**TableAdapter 查詢組態精靈**，您可能已選取新的 TableAdapter 的主要`Fill`查詢並不是其中一個TableAdapter 的其他查詢。 如需編輯 TableAdapter 的主要`Fill`查詢，請參閱 <<c2> [ 如何： 編輯 Tableadapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)。  
  
 ![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>若要編輯 TableAdapter 查詢  
  
1.  開啟中的資料集**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  選取您想要編輯 TableAdapter 查詢。  
  
3.  以滑鼠右鍵按一下 TableAdapter 查詢，然後選取**設定**。  
  
     **TableAdapter 查詢組態精靈**隨即開啟，供您修改查詢或預存程序，該查詢。  
  
4.  完成**TableAdapter 查詢組態精靈**與您想要的變更。 如需詳細資訊，請參閱 <<c0> [ 編輯 TableAdapters](../data-tools/editing-tableadapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)