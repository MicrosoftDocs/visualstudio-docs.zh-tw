---
title: 訊息檢視 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c421b7c22bed32e6c60d30098b2c19e0d71a0af3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="messages-view"></a>訊息檢視
每個視窗都有相關聯的訊息資料流。 訊息檢視 視窗會顯示此訊息資料流。 視窗控制代碼、 訊息碼和訊息會顯示。 您可以建立執行緒或處理序的訊息檢視。 這可讓您檢視傳送至特定處理程序或特別適用於捕捉視窗初始化訊息的執行緒所擁有的所有 windows 訊息。  
  
 一般的 [訊息] 檢視視窗下方會出現。 請注意，第一個資料行包含的視窗控制代碼，而且第二個資料行包含訊息碼 (詳見[訊息代碼](../debugger/message-codes.md))。 已解碼的訊息參數和傳回值會在右邊。  
  
 ![Spy #43; &#43;訊息檢視](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView")  
Spy++ 訊息檢視  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>若要開啟的視窗、 處理序或執行緒的訊息檢視  
  
1.  焦點移至[視窗檢視](../debugger/windows-view.md)，[處理序檢視](../debugger/processes-view.md)，或[執行緒檢視](../debugger/threads-view.md)視窗。  
  
2.  找到您想要檢查其訊息的項目節點並加以選取。  
  
3.  從**Spy**功能表上，選擇**記錄檔訊息**。  
  
     [訊息選項對話方塊](../debugger/message-options-dialog-box.md)隨即開啟。  
  
4.  選取您想要顯示之訊息的選項。  
  
5.  按**確定**開始記錄訊息。  
  
     訊息檢視 視窗隨即開啟，而**訊息**功能表會加入至 Spy + + 工具列。 選取的選項而定，訊息就會開始串流處理到作用中的 [訊息] 檢視視窗。  
  
6.  當您有足夠的訊息時，選擇**停止記錄**從**訊息**功能表。  
  
## <a name="in-this-section"></a>本節內容  
 [控制訊息檢視](../debugger/how-to-control-messages-view.md)  
 說明如何管理訊息檢視。  
  
 [從尋找視窗開啟訊息檢視](../debugger/how-to-open-messages-view-from-find-window.md)  
 說明如何從尋找視窗對話方塊開啟訊息檢視。  
  
 [搜尋訊息檢視中的訊息](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 說明如何在訊息檢視中找到特定的訊息。  
  
 [啟動和停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 說明如何啟動和停止訊息記錄。  
  
 [訊息代碼](../debugger/message-codes.md)  
 定義訊息的訊息檢視中所列的程式碼。  
  
 [顯示訊息屬性](../debugger/how-to-display-message-properties.md)  
 如何顯示一則訊息的詳細資訊。  
  
## <a name="related-sections"></a>相關章節  
 [Spy++ 檢視](../debugger/spy-increment-views.md)  
 說明 windows、 訊息、 處理程序和執行緒的 Spy + + 樹狀結構檢視。  
  
 [使用 Spy++](../debugger/using-spy-increment.md)  
 介紹 Spy + + 工具，並說明如何使用它。  
  
 [訊息選項對話方塊](../debugger/message-options-dialog-box.md)  
 用來選取哪一個訊息會列在作用中的訊息檢視。  
  
 [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md)  
 用來尋找特定訊息在訊息檢視中的節點。  
  
 [訊息屬性對話方塊](../debugger/message-properties-dialog-box.md)  
 用來顯示訊息，訊息 檢視中選取的屬性。  
  
 [Spy++ 參考](../debugger/spy-increment-reference.md)  
 包含各節描述每個 Spy + + 功能表和對話方塊方塊。