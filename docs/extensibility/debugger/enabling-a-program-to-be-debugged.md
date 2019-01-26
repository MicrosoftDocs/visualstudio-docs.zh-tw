---
title: 啟用程式以進行偵錯 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8faa677e5893c0737bcd89db5567ef7459f6d07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953221"
---
# <a name="enable-a-program-to-be-debugged"></a>啟用要偵錯程式
您偵錯引擎 (DE) 可以偵錯程式之前，您必須先啟動 DE 或將它附加至現有的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)  
 討論如何以啟用要偵錯程式的第一個步驟取得的連接埠。  
  
 [註冊計劃](../../extensibility/debugger/registering-the-program.md)  
 說明啟用要偵錯程式的下一步： 登錄與連接埠。 註冊之後，才能偵錯程式藉由附加，或是在 just-in-time (JIT) 偵錯程序。  
  
 [附加至程式](../../extensibility/debugger/attaching-to-the-program.md)  
 說明下一步： 附加至程式的偵錯工具。  
  
 [啟動基礎附加](../../extensibility/debugger/launch-based-attachment.md)  
 描述啟動時附加至程式中，也就是自動啟動的 SDM。  
  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)  
 逐步引導您建立的偵錯引擎 (DE) 時所需的事件，並將它附加至程式。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 定義偵錯引擎 (DE)，並說明透過 DE 介面和它們會導致偵錯工具不同的作業模式之間轉換的方式實作的服務。