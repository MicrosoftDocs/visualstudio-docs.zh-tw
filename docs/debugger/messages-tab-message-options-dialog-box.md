---
title: 訊息索引標籤中，訊息選項對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f19da533d2ab13e7493eae53af8dea3af4e520df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474696"
---
# <a name="messages-tab-message-options-dialog-box"></a>訊息選項對話方塊、訊息索引標籤
使用**訊息**索引標籤，選取 [訊息類型] 清單中以[訊息檢視](../debugger/messages-view.md)，並指定訊息搜尋準則。 若要顯示[訊息選項對話方塊](../debugger/message-options-dialog-box.md)，選擇**記錄檔訊息**從**Spy**功能表。  
  
 一般而言，您先選取**訊息群組**，然後選取個別調整選取項目**訊息，以檢視**。 **所有**按鈕選取所有的訊息類型，而**無** 按鈕會清除所有類型。  
  
 下列設定都適用於**訊息** 索引標籤：  
  
 **要檢視的訊息**  
 選取檢視特定訊息。 當您建立新的 [訊息] 視窗時，它可以顯示所有的訊息。 當您篩選來自**訊息**索引標籤上，該篩選條件只適用於新的訊息，而不顯示在視窗檢視中的訊息。  
  
 **訊息群組**  
 選取檢視的訊息群組。 可用的群組包括：  
  
-   使用驗證碼大於或等於 WM_USER WM_USER:  
  
-   註冊： 向**RegisterWindowMessage**呼叫  
  
-   未知： 未知的訊息中介於範圍 0 到 (WM_USER-1)  
  
 請注意，這些**訊息群組**不會對應到特定的項目底下**訊息，以檢視**。 當您選取的群組時，選取項目是直接套用至訊息資料流。  
  
 灰色的核取方塊內**訊息群組**表示**訊息，以檢視**清單方塊中已修改該群組中的訊息; 不是所有的訊息類型，該群組中選取。  
  
 **將設定儲存為預設值**  
 將目前的設定，以供稍後使用儲存為訊息搜尋選項。 結束 Spy + + 時，也會儲存這些設定。