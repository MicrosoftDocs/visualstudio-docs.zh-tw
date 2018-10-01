---
title: 如何： 將全域查詢加入至 TableAdapter |Microsoft Docs
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488109"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>如何： 將全域查詢加入至 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*全域查詢*是傳回單一 （純量） 值或沒有值的 SQL 查詢。 一般而言，全域函式會執行資料庫作業，例如插入、 更新、 刪除和資訊，例如資料表或所有項目以特定順序的總費用中傳回的客戶計數的彙總。  
  
 您執行新增全域查詢**TableAdapter 查詢組態精靈**內在**Dataset 設計工具**。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>若要將全域查詢加入資料集  
  
1.  開啟中的資料集**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  拖曳**查詢**從**資料集**索引標籤**工具箱**拖曳到空白區域**Dataset 設計工具**。  
  
     [編輯 TableAdapters](../data-tools/editing-tableadapters.md)隨即開啟。  
  
3.  選擇要使用查詢的連接。 您可以從清單中選擇一個，或建立新的連接。 如果您建立新的連接時，您必須將它儲存至應用程式組態檔的選項。 如需詳細資訊，請參閱 <<c0> [ 如何： 儲存並編輯連接字串](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)。  
  
4.  選擇是否要使用 SQL 陳述式或預存程序。  
  
5.  選擇要使用的預存程序或在**選擇查詢類型**頁面的精靈中，選擇一種查詢，您想要然後按一下**下一步**。  
  
6.  提供查詢，以執行所需的工作，例如`SELECT COUNT(*) AS CustomerCount FROM Customers`。  
  
    > [!NOTE]
    >  將直接拖曳至查詢**Dataset 設計工具**會建立只會傳回純量 （單一） 值的方法。 當您選取的預存程序的查詢可能傳回一個以上的單一值時，由精靈所建立的方法只會傳回單一值。 例如，查詢可能會傳回所傳回資料的第一個資料列的第一個資料行。  
  
7.  完成精靈。查詢隨即加入至**Dataset 設計工具**。 如需執行查詢的資訊，請參閱[如何： 執行 TableAdapter 查詢](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593)。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [如何： 使用 Windows Forms BindingNavigator 控制項巡覽資料](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)