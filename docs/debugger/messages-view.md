---
title: 訊息檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3f67a8e354addef7aca298ebac3740702951a17
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869876"
---
# <a name="messages-view"></a>訊息檢視
每個視窗都具有相關聯的訊息資料流。 訊息檢視 視窗會顯示此訊息資料流。 視窗控制代碼、 訊息和訊息會顯示。 您可以建立執行緒或處理序的訊息檢視。 這可讓您檢視傳送給特定的處理程序或特別適用於擷取視窗初始化訊息的執行緒所擁有的所有視窗的訊息。  
  
 一般的 [訊息] 檢視視窗會出現下方。 請注意，第一個資料行包含視窗控制代碼，而第二個資料行包含訊息碼 (中所述[訊息碼](../debugger/message-codes.md))。 已解碼的訊息參數和傳回值會在右邊。  
  
 ![Spy&#43; &#43;訊息檢視](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView")  
Spy++ 訊息檢視  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>若要開啟的視窗、 處理序或執行緒的訊息檢視  
  
1.  焦點移至[Windows 檢視](../debugger/windows-view.md)，[處理序檢視](../debugger/processes-view.md)，或[執行緒檢視](../debugger/threads-view.md)視窗。  
  
2.  尋找您想要檢查其訊息的項目節點，並加以選取。  
  
3.  從**Spy**功能表上，選擇**記錄檔訊息**。  
  
     [訊息選項對話方塊](../debugger/message-options-dialog-box.md)隨即開啟。  
  
4.  選取您想要顯示之訊息的選項。  
  
5.  按下**確定**開始記錄訊息。  
  
     訊息檢視 視窗隨即開啟，而**訊息**功能表會加入至 Spy + + 工具列。 視選取的選項而定，訊息就會開始串流處理至作用中的 [訊息] 檢視視窗。  
  
6.  當您有足夠的訊息時，選擇**停止記錄**從**訊息**功能表。  
  
## <a name="in-this-section"></a>本節內容  
 [控制訊息檢視](../debugger/how-to-control-messages-view.md)  
 說明如何管理訊息檢視。  
  
 [從尋找視窗開啟訊息檢視](../debugger/how-to-open-messages-view-from-find-window.md)  
 說明如何從尋找視窗對話方塊中開啟訊息檢視。  
  
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
 用來選取哪一個訊息會列在作用中的 [訊息] 檢視。  
  
 [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md)  
 用來尋找特定的訊息在訊息檢視中的節點。  
  
 [訊息屬性對話方塊](../debugger/message-properties-dialog-box.md)  
 用來顯示訊息，在 [訊息] 檢視中選取的屬性。  
  
 [Spy++ 參考](../debugger/spy-increment-reference.md)  
 包含描述每個 Spy + + 功能表和對話方塊方塊中的區段。