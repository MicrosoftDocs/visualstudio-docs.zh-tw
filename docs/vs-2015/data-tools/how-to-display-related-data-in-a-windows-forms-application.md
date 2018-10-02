---
title: 如何： 顯示相關的資料在 Windows Forms 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fc62789860cc10f5c410849936715a8ef82eae3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498237"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>如何：在 Windows Forms 應用程式中顯示相關的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以顯示相關的資料的拖曳項目共用相同的主資料表節點，從[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單。 例如，如果您有資料來源，具有`Customers`資料表和相關`Orders`資料表中，您會看到兩個資料表 （在 [樹狀] 檢視中） 的最上層節點中**Zdroje dat**視窗。 依序展開`Customers`節點，使您所見的資料行中，您會注意到清單中的最後一個資料行是可展開的節點代表`Orders`資料表。 這個節點代表客戶相關的訂單。 這表示如果您想要建立表單，可讓您選取的客戶，然後顯示該客戶的訂單清單，您會將您想要從這個單一階層中顯示的項目。  
  
 ![顯示關聯性的資料來源視窗](../data-tools/media/datasources2.gif "DataSources2")  
建立資料繫結控制項顯示相關的記錄  
  
 ![影片連結](../data-tools/media/playvideo.gif "PlayVideo")如本主題的影片版本，請參閱[How do i： 更新關聯資料表](http://go.microsoft.com/fwlink/?LinkId=143527)。  
  
### <a name="to-create-controls-that-display-related-records"></a>若要建立顯示相關的記錄控制項  
  
1.  開啟您的表單中[Windows Form 設計工具](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)。  
  
2.  開啟**Zdroje dat**視窗。 如需詳細資訊，請參閱 <<c0> [ 如何： 開啟 [資料來源] 視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
3.  展開代表關聯性的父資料表的節點。 （父資料表是一對多關聯性的 「 一 」 端的資料表）。  
  
4.  將您想要從關聯性中的父資料表中顯示任何項的目拖曳**Zdroje dat**視窗拖曳至表單。  
  
5.  相關的子資料表會顯示為可展開的節點，在父資料表的資料行清單底部。 拖曳您想要從這類相關節點拖曳至表單中顯示的項目。  
  
    > [!NOTE]
    >  從最上層的節點中拖曳項目建立不相關的個別[BindingSource 元件](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)的方式無法促成巡覽相關的記錄。 若要將相關的資料繫結中，您必須選取資料表從相同的階層式節點。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [操作說明：使用 Windows Forms BindingNavigator 控制項巡覽資料](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)