---
title: 線上程視圖中搜尋執行緒 |Microsoft Docs
description: 在 Visual Studio 中進行偵錯工具時，使用執行緒識別碼或模組字串做為搜尋準則，在 Spy + + 工具的執行緒視圖中搜尋特定的執行緒。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92864c9d3c66a7547ef52a2694f6307d57a43304
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148529"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>如何：在執行緒檢視中搜尋執行緒
您可以使用執行緒識別碼或模組字串做為搜尋準則，線上程視圖中搜尋特定的執行緒。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會線上程樹狀結構中顯示所選執行緒的屬性。

### <a name="to-search-for-a-thread-in-threads-view"></a>線上程視圖中搜尋執行緒

1. 排列視窗，讓 Spy + + 和作用中 [執行緒的視圖](../debugger/threads-view.md) 視窗可見。

2. 在 [ **搜尋** ] 功能表中，選擇 [ **尋找執行緒**]。

    [ [執行緒搜尋] 對話方塊](../debugger/thread-search-dialog-box.md) 隨即開啟。

3. 輸入執行緒識別碼或模組字串做為搜尋準則。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要尋找模組所擁有的所有線程，請清除 [ **執行緒** ] 文字方塊，並在 [ **模組** ] 方塊中輸入模組名稱。 然後使用 **[尋找下一個]** 繼續搜尋執行緒。

5. 選擇 [ **向上** ] 或 [ **向下** ] 以取得搜尋的初始方向。

6. 按一下 [確定]。

   如果找到相符的執行緒，則會在 [執行緒] 視圖視窗中反白顯示。