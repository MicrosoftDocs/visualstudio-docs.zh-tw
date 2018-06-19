---
title: 訊息代碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474439"
---
# <a name="message-codes"></a>訊息代碼
中所示的每個訊息列[訊息檢視](../debugger/messages-view.md)包含 'P' 的 '的' 或 'R' 程式碼。 這些代碼具有以下意義：  
  
|程式碼|意義|  
|----------|-------------|  
|P|將訊息公佈到佇列**PostMessage**函式。 不未提供有關訊息的最後配置的任何資訊。|  
|S|傳送訊息時，使用**SendMessage**函式。 這表示直到接收者處理，並傳回訊息寄件者不會回復控制。 收件者可以因此，成功的傳回值傳回給寄件者。|  
|秒|訊息已傳送，但安全性會防止存取的傳回值。|  
|R|每個的 ' 行有相對應的 'R' （返回） 行列出訊息的傳回值。 有時候訊息呼叫為巢狀，這表示該訊息處理常式會傳送另一則訊息。|