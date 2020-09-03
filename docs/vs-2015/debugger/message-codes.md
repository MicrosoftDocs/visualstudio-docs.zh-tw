---
title: 訊息碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182955"
---
# <a name="message-codes"></a>訊息代碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[訊息視圖](../debugger/messages-view.md)中顯示的每個消息行都包含 ' P '、' ' '、' ' ' 或 ' R ' 程式碼。 這些代碼具有下列意義：  
  
|程式碼|意義|  
|----------|-------------|  
|P|已使用 **PostMessage** 函式將訊息張貼至佇列。 關於訊息的終極處置沒有任何資訊可供使用。|  
|S|訊息是使用 **SendMessage** 函式傳送。 這表示寄件者不會重新取得控制權，直到接收者處理並傳回訊息為止。 因此接收者可以將傳回值傳回給寄件者。|  
|s|訊息已傳送，但安全性可防止存取傳回值。|  
|R|每個 ' 行都有對應的 ' R ' (傳回列出訊息傳回值的) 行。 有時訊息呼叫會進行嵌套，這表示一個訊息處理常式會傳送另一則訊息。|
