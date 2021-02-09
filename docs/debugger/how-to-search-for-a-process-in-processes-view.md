---
title: 在進程視圖中搜尋進程 |Microsoft Docs
description: 在 [Spy + +] 工具的 [進程] 視圖中搜尋特定進程，方法是在 Visual Studio 中的偵錯工具時，使用其處理序識別碼或模組字串做為搜尋準則。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845070"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>如何：在處理序檢視中搜尋處理序
您可以使用處理序識別碼或模組字串做為搜尋準則，在進程視圖中搜尋特定的進程。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會在進程樹狀結構中顯示所選進程的屬性。

### <a name="to-search-for-a-process-in-processes-view"></a>在進程視圖中搜尋進程

1. 排列您的視窗，讓 Spy + + 和作用中 [進程視圖](../debugger/processes-view.md) 視窗可見。

2. 從 [**搜尋**] 功能表中，選擇 [**尋找進程**]

    [ [進程搜尋] 對話方塊](../debugger/process-search-dialog-box.md) 隨即開啟。

3. 輸入處理常式識別碼或模組字串做為搜尋準則。

4. 清除您不想要指定值的任何欄位。

   > [!TIP]
   > 若要尋找模組所擁有的所有進程，請清除 [ **處理** ] 方塊，然後在 [ **模組** ] 方塊中輸入模組名稱。 然後使用 **[尋找下一個]** 繼續搜尋進程。

5. 選擇 [ **向上** ] 或 [ **向下** ] 以取得搜尋的初始方向。

6. 按一下 [確定]  。

   如果找到相符的進程，就會在 [進程] **視圖** 視窗中反白顯示。