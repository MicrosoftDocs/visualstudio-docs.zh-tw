---
title: 訊息選項對話方塊、輸出索引標籤 |Microsoft Docs
description: 使用 [訊息選項] 的 [輸出] 索引標籤，即可指定訊息中顯示的訊息資料。 本文描述可用的設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9cb48f061cfda78e3dec8ef515df82fdefb8193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891575"
---
# <a name="output-tab-message-options-dialog-box"></a>訊息選項對話方塊、輸出索引標籤
使用 [ **輸出** ] 索引標籤，即可指定要在 [訊息視圖](../debugger/messages-view.md)中列出的每個訊息的資料。 若要顯示 [[訊息選項] 對話方塊](../debugger/message-options-dialog-box.md)，請從 [ **Spy** ] 功能表選擇 [**記錄訊息**]。

 [ **輸出** ] 索引標籤提供下列設定：

 **行號** 顯示行號。

 **訊息的嵌套層級** 在每個層級各有一個句點的嵌套訊息前置詞。

 **原始訊息參數** 顯示十六進位的 **wParam** 和 **lParam** 值。

 **解碼的訊息參數** 顯示 **wParam** 和 **lParam** 值之訊息特定解碼的結果。

 **原始傳回值** 顯示十六進位 **lResult** 傳回值。

 **解碼** 的傳回值顯示 **lResult** 傳回值之訊息特定解碼的結果。

 **訊息來源時間** 自 Windows 系統啟動以來經過的時間， (只) 張貼的訊息。

 **訊息滑鼠位置** 只有) 張貼的訊息，將訊息張貼 (時，滑鼠的螢幕座標。

 **最大行數** 限制目前選取的訊息 view 中保留的行數。

 **也將訊息記錄到** 檔案指定訊息記錄檔的輸出檔。 這個輸出檔會與 [訊息記錄] 視窗同時寫入。

 **將設定儲存為預設值** 針對新的訊息串流視窗儲存先前的設定。 這些設定會在您結束 Spy + + 時儲存。