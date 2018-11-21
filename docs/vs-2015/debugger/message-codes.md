---
title: 訊息代碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0464042c17a3ed0836b99183dacbe4918823c752
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724640"
---
# <a name="message-codes"></a>訊息代碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

顯示在每個訊息列[訊息檢視](../debugger/messages-view.md)包含 'P' 的 '的' 或 'R' 程式碼。 這些程式碼具有下列意義：  
  
|程式碼|意義|  
|----------|-------------|  
|P|公佈訊息至佇列，並**PostMessage**函式。 不未提供有關訊息的最後配置的任何資訊。|  
|S|已傳送訊息，使用**SendMessage**函式。 這表示直到接收者處理，並傳回訊息寄件者不會取回控制權。 接收者可以因此，將傳回的值傳遞回給寄件者。|  
|秒|訊息已傳送，但安全性可防止存取傳回的值。|  
|R|每個的 ' 一行有相對應的 'R' （返回） 行列出訊息的傳回值。 有時候訊息呼叫為巢狀，這表示該一則訊息處理常式會傳送另一則訊息。|



