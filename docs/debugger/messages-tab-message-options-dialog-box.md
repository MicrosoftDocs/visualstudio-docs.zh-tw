---
title: 訊息索引標籤中，訊息選項對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f7675039f8e5f5fb5c1d5899b96682ab60a2bc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830585"
---
# <a name="messages-tab-message-options-dialog-box"></a>訊息選項對話方塊、訊息索引標籤
使用**訊息**索引標籤，選取 [到] 清單中的哪些訊息類型[訊息檢視](../debugger/messages-view.md)，並指定訊息的搜尋準則。 若要顯示[訊息選項對話方塊](../debugger/message-options-dialog-box.md)，選擇**記錄檔訊息**從**Spy**功能表。  
  
 一般而言，您先選取**訊息群組**，然後選取 個別調整選取項目**訊息，以檢視**。 **所有** 按鈕會選取所有的訊息類型，而**無** 按鈕會清除所有型別。  
  
 下列設定位於**訊息** 索引標籤：  
  
 **要檢視的訊息**  
 選取檢視特定的訊息。 當您建立新的 [訊息] 視窗時，它可以顯示所有訊息。 當您篩選來自**訊息**索引標籤上，該篩選條件只適用於新的訊息，而不顯示在 [Windows] 檢視中的訊息。  
  
 **訊息群組**  
 選取檢視的訊息群組。 可用的群組包含：  
  
- 使用程式碼大於或等於 WM_USER WM_USER:  
  
- 註冊： 向**RegisterWindowMessage**呼叫  
  
- 未知： 範圍介於 0 到 (WM_USER-1) 中的未知的訊息  
  
  請注意，這些**訊息群組**不會對應至特定的項目底下**訊息，以檢視**。 當您選取的群組時，選取項目是直接套用到訊息資料流。  
  
  灰色的核取方塊內**訊息群組**指出**訊息，以檢視**清單方塊是否變更過的該群組中的訊息; 不是所有的訊息類型，該群組中選取。  
  
  **將設定另存成預設**  
  儲存目前的設定，以供稍後使用，做為訊息搜尋選項。 結束 Spy + + 時，也會儲存這些設定。