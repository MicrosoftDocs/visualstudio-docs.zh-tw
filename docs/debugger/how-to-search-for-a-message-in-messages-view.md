---
title: 如何-在訊息視圖中搜尋訊息 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7145732ef635d550aa883603b0f56090eb6d1278
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349311"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>如何：在訊息檢視中搜尋訊息
您可以使用其控制碼、類型或訊息識別碼作為搜尋準則，在 [訊息] 視圖中搜尋特定訊息。 其中任何一項（或組合）都是有效的搜尋準則。 也可以指定搜尋的初始方向。 對話方塊中的欄位會預先載入目前選取之訊息的屬性。

### <a name="to-search-for-a-message-in-messages-view"></a>若要在訊息視圖中搜尋訊息

1. 排列視窗，讓 [Spy + +] 和 [作用中[訊息] 視圖](../debugger/messages-view.md)視窗可見。

2. 從 [**搜尋**] 功能表中，選擇 [**尋找訊息**]。

    [[訊息搜尋] 對話方塊](../debugger/message-search-dialog-box.md)隨即開啟。

3. 將搜尋**工具**拖曳到所需的視窗上。 當您拖曳工具時，[**訊息搜尋**] 對話方塊會顯示所選視窗的詳細資料。

   - 或 -

     如果您有想要檢查其訊息的視窗控制碼，請在 [**控制碼**] 文字方塊中輸入它。

   - 或 -

     如果您知道所需的訊息類型和/或訊息識別碼，請從 [**類型**] 和 [**訊息**] 下拉式功能表中選取它們，然後清除 [**控制碼**] 文字方塊。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要減少螢幕雜亂，請選取 [**隱藏 Spy** ] 選項。 此選項會隱藏主 Spy + + 視窗，而只會在其他應用程式頂端顯示 [**尋找視窗**] 對話方塊。 當您按一下 **[確定]** 或 [**取消**] 時，或清除 [**隱藏 Spy + +** ] 選項時，就會還原 Spy + + 主視窗。

5. 針對搜尋的初始方向，選擇 [**向上**] 或 [**向下**]。

6. 按一下 [確定]。

   如果找到相符的訊息，則會在 [訊息] 視圖視窗中反白顯示。 請參閱[訊息視圖](../debugger/messages-view.md)。