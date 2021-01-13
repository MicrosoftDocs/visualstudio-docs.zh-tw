---
title: 在訊息視圖中搜尋訊息 |Microsoft Docs
description: 在 [Spy + +] 工具的 [訊息] 視圖中搜尋特定訊息，方法是在 Visual Studio 中的偵錯工具時，使用其控制碼、類型或訊息識別碼作為搜尋準則。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c351eacc6fc3793065bcd11eb5456eebdc1864f3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148581"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>如何：在訊息檢視中搜尋訊息
您可以使用控制碼、類型或訊息識別碼作為搜尋準則，在 [訊息] 視圖中搜尋特定的訊息。 其中任何一個（或組合）都是有效的搜尋準則。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會預先載入目前選取的訊息屬性。

### <a name="to-search-for-a-message-in-messages-view"></a>在訊息視圖中搜尋訊息

1. 排列視窗，讓 Spy + + 和使用中的 [訊息查看](../debugger/messages-view.md) 視窗都可見。

2. 在 [ **搜尋** ] 功能表中，選擇 [ **尋找訊息**]。

    [ [訊息搜尋] 對話方塊](../debugger/message-search-dialog-box.md) 隨即開啟。

3. 將 [ **Finder] 工具** 拖曳至想要的視窗。 當您拖曳工具時，[ **訊息搜尋** ] 對話方塊會顯示所選視窗的詳細資料。

   - 或 -

     如果您有要檢查其訊息的視窗控制碼，請將它輸入 [ **控制碼** ] 文字方塊中。

   - 或 -

     如果您知道您想要的訊息類型及/或訊息識別碼，請從 [ **類型** ] 和 [ **訊息** ] 下拉式功能表中選取它們，然後清除 [ **控制碼** ] 文字方塊。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要減少螢幕混亂，請選取 [ **隱藏 Spy** ] 選項。 此選項會隱藏主要的 Spy + + 視窗，讓 [ **尋找視窗** ] 對話方塊只會顯示在其他應用程式的頂端。 當您按一下 **[確定] 或 [** **取消**]，或清除 [ **隱藏 spy + +** ] 選項時，就會還原 Spy + + 主視窗。

5. 選擇 [ **向上** ] 或 [ **向下** ] 以取得搜尋的初始方向。

6. 按一下 [確定]。

   如果找到相符的訊息，則會在 [訊息] 視圖視窗中反白顯示。 查看 [訊息的觀點](../debugger/messages-view.md)。