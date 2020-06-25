---
title: 如何-在進程視圖中搜尋進程 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e823ecb1f7523c1a6f094d5669f4a37a72e84f60
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349285"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>如何：在處理序檢視中搜尋處理序
您可以使用處理序識別碼或模組字串做為搜尋準則，在進程視圖中搜尋特定進程。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會在進程樹狀結構中顯示所選取進程的屬性。

### <a name="to-search-for-a-process-in-processes-view"></a>在進程視圖中搜尋進程

1. 排列視窗，讓 [Spy + +] 和 [作用中[進程] 視圖](../debugger/processes-view.md)視窗可見。

2. 從 [**搜尋**] 功能表中，選擇 [**尋找進程**]

    [[處理搜尋] 對話方塊](../debugger/process-search-dialog-box.md)隨即開啟。

3. 輸入處理序識別碼或模組字串做為搜尋準則。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要尋找模組所擁有的所有進程，請清除 [**進程**] 方塊，並在 [**模組**] 方塊中輸入模組名稱。 然後使用 **[尋找下一個]** 繼續搜尋處理常式。

5. 針對搜尋的初始方向，選擇 [**向上**] 或 [**向下**]。

6. 按一下 [確定]。

   如果找到相符的進程，則會在 [**進程視圖**] 視窗中反白顯示。