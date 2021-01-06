---
title: 訊息視圖 |Microsoft Docs
description: 每個視窗、執行緒和進程都有相關聯的訊息資料流程，可在 [訊息] 視窗中看到。 瞭解如何開啟和控制訊息的查看。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 692902b2d2b612c71c2d1dc0f936c7550f430847
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903399"
---
# <a name="messages-view"></a>訊息檢視
每個視窗都有相關聯的訊息資料流程。 [訊息] 視圖視窗會顯示此訊息資料流程。 系統會顯示視窗控制碼、訊息程式碼和訊息。 您也可以建立執行緒或進程的訊息查看。 這可讓您查看傳送至特定進程或執行緒所擁有之所有 windows 的訊息，這在捕獲視窗初始化訊息時特別有用。

 一般的 [訊息] 視圖視窗如下所示。 請注意，第一個資料行包含視窗控制碼，而第二個數據行包含訊息程式碼 (在) 的 [訊息](../debugger/message-codes.md) 代碼中說明。 已解碼的訊息參數和傳回值位於右邊。

 ![Spy&#43;&#43; 訊息視圖](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView") Spy + + 訊息視圖

## <a name="procedures"></a>程序

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>開啟視窗、進程或執行緒的訊息視圖

1. 將焦點移至 [Windows View](../debugger/windows-view.md)、 [進程視圖](../debugger/processes-view.md)或執行緒的 [視圖](../debugger/threads-view.md) 視窗。

2. 找出您想要檢查其訊息的專案節點，然後選取它。

3. 從 **Spy** 功能表選擇 [ **記錄檔訊息**]。

     [ [訊息選項] 對話方塊](../debugger/message-options-dialog-box.md) 隨即開啟。

4. 選取您要顯示之訊息的選項。

5. 按下 **[確定]** 開始記錄訊息。

     [訊息] 視圖視窗隨即開啟，而且 [ **訊息** ] 功能表會加入至 Spy + + 工具列。 視選取的選項而定，訊息會開始串流至 [使用中訊息] 視窗。

6. 當您有足夠的訊息時，請從 [**訊息**] 功能表選擇 [**停止記錄**]。

## <a name="in-this-section"></a>本節內容
 [控制訊息的視圖](../debugger/how-to-control-messages-view.md) 說明如何管理訊息查看。

 [從尋找視窗開啟訊息查看](../debugger/how-to-open-messages-view-from-find-window.md) 說明如何從 [尋找視窗] 對話方塊開啟訊息查看。

 [在訊息視圖中搜尋訊息](../debugger/how-to-search-for-a-message-in-messages-view.md) 說明如何在訊息視圖中尋找特定的訊息。

 [啟動和停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md) 說明如何啟動和停止訊息記錄。

 [訊息代碼](../debugger/message-codes.md) 定義訊息查看中所列訊息的代碼。

 [顯示訊息屬性](../debugger/how-to-display-message-properties.md) 如何顯示訊息的詳細資訊。

## <a name="related-sections"></a>相關章節
 [Spy + + Views](../debugger/spy-increment-views.md) 說明 windows、訊息、進程和執行緒的 Spy + + 樹狀檢視。

 [使用 Spy + +](../debugger/using-spy-increment.md) 介紹 Spy + + 工具，並說明其使用方式。

 [[訊息選項] 對話方塊](../debugger/message-options-dialog-box.md)用來選取要在使用中的訊息查看中列出的訊息。

 [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md) 用來尋找訊息 view 中特定訊息的節點。

 [訊息屬性對話方塊](../debugger/message-properties-dialog-box.md) 用來顯示在訊息查看中選取的訊息屬性。

 [Spy + + 參考](../debugger/spy-increment-reference.md) 包含描述每個 Spy + + 功能表和對話方塊的章節。