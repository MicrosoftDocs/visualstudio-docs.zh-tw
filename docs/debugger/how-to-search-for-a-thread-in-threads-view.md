---
title: 如何線上程視圖中搜尋執行緒 |Microsoft Docs
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
ms.openlocfilehash: e97d381fd0b1f6340035eec129e7304a8e73b03d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349259"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>如何：在執行緒檢視中搜尋執行緒
您可以使用執行緒識別碼或模組字串做為搜尋準則，在 [執行緒] 視圖中搜尋特定的執行緒。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會線上程樹狀結構中顯示所選取執行緒的屬性。

### <a name="to-search-for-a-thread-in-threads-view"></a>若要線上程視圖中搜尋執行緒

1. 排列視窗，讓 [Spy + +] 和 [作用中的[執行緒](../debugger/threads-view.md)] 視窗可見。

2. 從 [**搜尋**] 功能表中，選擇 [**尋找執行緒**]。

    [[執行緒搜尋] 對話方塊](../debugger/thread-search-dialog-box.md)隨即開啟。

3. 輸入執行緒識別碼或模組字串做為搜尋準則。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要尋找模組擁有的所有線程，請清除 [**執行緒**] 文字方塊，然後在 [**模組**] 方塊中輸入模組名稱。 然後使用 **[尋找下一個]** 繼續搜尋執行緒。

5. 針對搜尋的初始方向，選擇 [**向上**] 或 [**向下**]。

6. 按一下 [確定]。

   如果找到相符的執行緒，則會在 [執行緒] 視圖視窗中反白顯示。