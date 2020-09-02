---
title: 訊息選項對話方塊、訊息索引標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149443"
---
# <a name="messages-tab-message-options-dialog-box"></a>訊息選項對話方塊、訊息索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [ **訊息** ] 索引標籤，即可選取要在 [訊息視圖](../debugger/messages-view.md)中列出的訊息類型，以及指定訊息搜尋準則。 若要顯示 [[訊息選項] 對話方塊](../debugger/message-options-dialog-box.md)，請從 [ **Spy** ] 功能表選擇 [**記錄訊息**]。  
  
 一般來說，您會先選取 [ **訊息群組**]，然後選取 **要查看的個別訊息來**微調選取範圍。 [ **全部** ] 按鈕會選取所有訊息類型，而 [ **無** ] 按鈕則會清除所有類型。  
  
 [ **訊息** ] 索引標籤上提供下列設定：  
  
 **要檢視的訊息**  
 選取要查看的特定訊息。 當您建立新的 [訊息] 視窗時，它可以顯示所有訊息。 當您從 [ **訊息** ] 索引標籤篩選訊息時，該篩選只會套用至新的訊息，而不會套用到已在 Windows view 中顯示的訊息。  
  
 **訊息群組**  
 選取要查看的訊息群組。 可用的群組包括：  
  
- WM_USER：程式碼大於或等於 WM_USER  
  
- 已註冊：已向 **RegisterWindowMessage** 呼叫註冊  
  
- 未知：範圍0到 (的未知訊息 WM_USER – 1)   
  
  請注意，這些 **訊息群組** 不會對應到 **要查看的訊息**底下的特定專案。 當您選取群組時，選取專案會直接套用至訊息串流。  
  
  在 [ **訊息群組** ] 內有一個灰色的核取方塊，表示已針對該群組中的訊息修改 [ **要查看的訊息** ] 清單方塊;未選取該群組中的所有訊息類型。  
  
  [將設定另存成預設]****  
  儲存目前的設定，以供稍後用來作為訊息搜尋選項。 當結束 Spy + + 時，也會儲存這些設定。
