---
title: 如何-從尋找視窗開啟訊息視圖 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3258e45e47c263912957ff5066ea9d02ad03e57e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349480"
---
# <a name="how-to-open-messages-view-from-find-window"></a>如何：從尋找視窗開啟訊息檢視
您可能會發現使用 [**尋找視窗**] 對話方塊來選取目標視窗，然後開啟該視窗的 [訊息] 視圖，會很方便。

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>使用 [尋找視窗] 對話方塊開啟 [訊息] 視圖視窗

1. 排列視窗，讓 Spy + + 和目標視窗都可以看到。

2. 從**Spy**功能表中，選擇 [**尋找視窗]**。

    [[尋找視窗] 對話方塊](../debugger/find-window-dialog-box.md)隨即開啟。

3. 從 [ **Windows** ] 索引標籤中，將搜尋**工具**拖曳到目標視窗上。 當您拖曳工具時，[**尋找視窗**] 對話方塊會顯示所選視窗的詳細資料。

   - 或 -

     如果您有想要檢查的視窗控制碼（例如，從偵錯工具複製），您可以在 [**控制碼**] 文字方塊中輸入它。

4. 在 [**顯示**] 底下，選取 [**訊息**]。

5. 按下 **[確定]**。

    [空白[訊息] 視圖](../debugger/messages-view.md)視窗隨即開啟，而且 [**訊息**] 功能表會加入至 Spy + + 工具列。

6. 從 [**訊息**] 功能表中，選擇 [**記錄選項**]。

    [[訊息選項] 對話方塊](../debugger/message-options-dialog-box.md)隨即開啟。

7. 選取您想要顯示之訊息的選項。

8. 按 **[確定]** 開始記錄訊息。

    視選取的選項而定，訊息會開始串流至 [使用中的訊息] 視圖視窗。

9. 當您有足夠的訊息時，請從 [**訊息**] 功能表選擇 [**停止記錄**]。
