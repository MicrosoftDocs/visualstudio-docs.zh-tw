---
title: 訊息屬性對話方塊 |Microsoft Docs
description: 請參閱訊息屬性，以找出訊息的詳細資訊，而不是訊息查看中顯示的訊息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f58ad7344c7de9a9486fcb3ccefbf263688926f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903060"
---
# <a name="message-properties-dialog-box"></a>訊息屬性對話方塊
使用此對話方塊可深入瞭解特定的訊息。 若要顯示此對話方塊，請將焦點移至 [ [訊息] 視圖](../debugger/messages-view.md) 視窗。 選取樹狀結構中的任何訊息節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。

 [ **一般** ] 索引標籤是唯一顯示的索引標籤。 可用的設定如下：

 **視窗控制碼** 此視窗的唯一識別碼。 視窗控制碼號碼會重複使用;他們只會在該視窗的存留期內找出一個視窗。 按一下此值以查看這個視窗的屬性。

 **嵌套層級** 此訊息的嵌套深度，其中0是無嵌套。

 **訊息** 所選 windows 訊息的數目、狀態和名稱。

 **lResult***LResult* 參數的值（如果有的話）。

 **wParam***WParam* 參數的值（如果有的話）。

 **lParam***LParam* 參數的值（如果有的話）。 如果這個值是字串或結構的指標，則會將其解碼。

## <a name="related-sections"></a>相關章節
 [[訊息選項] 對話方塊](../debugger/message-options-dialog-box.md)用來選取要在使用中的訊息查看中列出的訊息。

 [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md) 用來尋找訊息 view 中特定訊息的節點。

 [Spy + + 參考](../debugger/spy-increment-reference.md) 包含描述每個 Spy + + 功能表和對話方塊的章節。

 [從尋找視窗開啟訊息查看](../debugger/how-to-open-messages-view-from-find-window.md) 說明如何從 [尋找視窗] 對話方塊開啟訊息查看。

 [在訊息視圖中搜尋訊息](../debugger/how-to-search-for-a-message-in-messages-view.md) 說明如何在訊息視圖中尋找特定的訊息。

 [訊息視圖](../debugger/messages-view.md) 顯示與視窗、進程或執行緒相關聯的訊息資料流程。

 [Spy + + Views](../debugger/spy-increment-views.md) 說明 windows、訊息、進程和執行緒的 Spy + + 樹狀檢視。

 [使用 Spy + +](../debugger/using-spy-increment.md) 介紹 Spy + + 工具，並說明其使用方式。