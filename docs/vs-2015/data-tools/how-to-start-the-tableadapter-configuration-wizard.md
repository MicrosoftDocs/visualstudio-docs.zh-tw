---
title: 如何： 啟動 TableAdapter 組態精靈 |Microsoft Docs
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7f603789014239762f564c3b2391b99865d8f620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261887"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>如何：啟動 TableAdapter 組態精靈
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**TableAdapter 組態精靈**建立及編輯 TableAdapters 在強類型資料集。 此精靈會根據您輸入至精靈的 SQL 陳述式，或是根據資料庫中的現有預存程序，建立 TableAdapters。 精靈也可以根據您輸入至精靈的 SQL 陳述式，建立新的預存程序。  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>啟動 TableAdapter 組態精靈以建立新的 TableAdapter  
  
1.  開啟您的資料集，在**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
    > [!NOTE]
    >  如果您沒有在專案中的資料集，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
2.  如果您要建立新的 TableAdapter，拖曳**TableAdapter**物件**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**.  
  
3.  在 **選擇資料連接**頁面上，選取資料連接，從清單中目前可用的連線，或選取**新的連接**以建立新的連接。  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>啟動 TableAdapter 組態精靈以編輯現有的 TableAdapter  
  
1.  開啟您的資料集，在**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  以滑鼠右鍵按一下 在 TableAdapter **Dataset 設計工具**，然後選擇**設定**。 精靈會開啟**產生 SQL 陳述式**頁面或**命令繫結至現有的預存程序**頁面上，視 TableAdapter 原先設定的方式而定。  
  
3.  完成精靈。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [如何： 排序和篩選 ADO.NET 資料使用 Windows Forms BindingSource 元件](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [如何： 使用 Windows Forms BindingSource 元件建立查閱資料表](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)