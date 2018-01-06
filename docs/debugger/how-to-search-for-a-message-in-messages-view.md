---
title: "如何： 搜尋訊息檢視中的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df8fc9ee13a721f98a942a3bb6d10f6c8d844ddf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>如何：在訊息檢視中搜尋訊息
您可以搜尋特定訊息在訊息檢視中，使用其控制代碼、 類型或訊息識別碼，做為搜尋準則。 其中任何一個，或組合，將會是有效的搜尋準則。 也可以指定搜尋的初始方向。 在對話方塊中的欄位會預先載入的目前選取的訊息屬性。  
  
### <a name="to-search-for-a-message-in-messages-view"></a>若要搜尋的訊息檢視中的訊息  
  
1.  排列的視窗，因此該 Spy + + 和作用中[訊息檢視](../debugger/messages-view.md)視窗會顯示。  
  
2.  從**搜尋**功能表上，選擇**尋找訊息**。  
  
     [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md)隨即開啟。  
  
3.  拖曳**搜尋工具**透過所需的視窗。 當您拖曳工具，**訊息搜尋** 對話方塊上選取的視窗中顯示詳細資料。  
  
     - 或 -  
  
     如果您有您想要檢查其訊息的視窗控制代碼時，將它輸入**處理**文字方塊。  
  
     - 或 -  
  
     如果您知道訊息類型和/或您想要的訊息 ID，則選取從**類型**和**訊息**下拉式功能表，然後清除**處理**文字方塊。  
  
4.  清除所有的欄位，您不想指定值。  
  
    > [!TIP]
    >  若要減少螢幕混亂的情形，請選取**隱藏 spy + +**選項。 此選項會隱藏主要 Spy + + 視窗中，只留下**尋找視窗**對話方塊在其他應用程式的上層。 當您按一下 還原 Spy + + 主視窗**確定**或**取消**，或當您清除**隱藏 Spy + +**選項。  
  
5.  選擇**向上**或**向**搜尋初始方向。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
 如果找到符合的訊息，它會反白顯示在訊息的 [檢視] 視窗。 請參閱[訊息檢視](../debugger/messages-view.md)。