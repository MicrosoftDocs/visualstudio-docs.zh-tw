---
title: 如何： 建立 TableAdapter 查詢 |Microsoft Docs
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f7d4bd84d5cd4538d06048fd6953fa95fc344da0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490947"
---
# <a name="how-to-create-tableadapter-queries"></a>如何：建立 TableAdapter 查詢
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter 查詢是 SQL 陳述式或您的應用程式可以對資料庫執行的預存程序。  
  
 盡可能將查詢加入至 TableAdapter 根據您的應用程式的需要。 TableAdapter 查詢會顯示為 TableAdapter 上的方法。 當您建立查詢，稱為`FillByCity`採用參數，代表縣 （市） 值，將查詢加入至 TableAdapter。 它會成為會做為引數的參數的正確類型的具類型方法，在此情況下代表縣 （市） 值的字串。 在任何物件上呼叫 TableAdapter 查詢，就像任何方法一樣。 例如，下列程式碼執行`FillByCity`查詢與填滿`Customers`縣 （市） 值為所有客戶資料表`Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 TableAdapter 查詢可能會填滿資料表 (`Fill`並`FillBy`查詢) 或傳回查詢所傳回的資料填入新的資料表 (`GetData`和`GetDataBy`查詢)。  
  
 可以藉由執行將查詢加入至現有的 TableAdapters[編輯 TableAdapters](../data-tools/editing-tableadapters.md)。 (任何 TableAdapter 上按一下滑鼠右鍵，然後選擇 **加入查詢**。)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>在 Dataset 設計工具中建立查詢  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>若要將查詢加入資料集設計工具中的 TableAdapter  
  
1.  開啟中的資料集**Dataset 設計工具**。 如需詳細資訊，請參閱 <<c0> [ 如何： 以 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2.  以滑鼠右鍵按一下所需的 TableAdapter，並選取**加入查詢**。  
  
     -或-  
  
3.  拖曳**查詢**從**資料集**索引標籤**工具箱**拖曳到設計工具中的資料表。  
  
     **TableAdapter 查詢組態精靈**隨即開啟。  
  
4.  完成精靈。將查詢加入至 TableAdapter。  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>直接在您的 Windows 應用程式中的表單上建立查詢  
 如果您的表單上有 TableAdapter 的執行個體表示您可以加入查詢，使用[搜尋準則產生器 對話方塊中](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)，它會將新增<xref:System.Windows.Forms.ToolStrip>表單接受任何輸入參數的查詢，所需的指導方針，以及若要執行查詢 按鈕。  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>若要將查詢加入至 TableAdapter，使用 [搜尋條件] 對話方塊  
  
1.  選取在元件匣中的 TableAdapter。  
  
2.  按一下 TableAdapter 的智慧標籤，然後選擇**加入查詢**。  
  
3.  完成 [] 對話方塊中，並將查詢加入至 TableAdapter。 如需詳細資訊，請參閱 <<c0> [ 搜尋準則產生器對話方塊](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何： 編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [加入新的資料來源](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [如何： 使用 Windows Forms BindingNavigator 控制項巡覽資料](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [逐步解說：以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)