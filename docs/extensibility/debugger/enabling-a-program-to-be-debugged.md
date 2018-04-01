---
title: 啟用程式進行偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a581c5a9ae56f52727c011db1de2ad35a5ba3592
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-a-program-to-be-debugged"></a>啟用要進行偵錯的程式
您偵錯引擎 (DE) 偵錯程式之前，必須先啟動 DE，或將它附加至現有的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)  
 討論如何以啟用偵錯程式的第一個步驟取得的連接埠。  
  
 [註冊程式](../../extensibility/debugger/registering-the-program.md)  
 說明啟用偵錯程式的下一個步驟： 註冊與連接埠。 一旦註冊，才能偵錯程式藉由附加，或在 just-in-time (JIT) 偵錯的程序。  
  
 [附加至程式](../../extensibility/debugger/attaching-to-the-program.md)  
 說明 下一步： 偵錯工具附加至程式。  
  
 [啟動基礎附加](../../extensibility/debugger/launch-based-attachment.md)  
 描述啟動基礎附件會自動在 SDM 所啟動程式。  
  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)  
 帶領您逐步建立偵錯引擎 (DE) 時所需的事件，並將它附加至程式。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 定義偵錯引擎 (DE)，並說明透過 DE 介面和它們會導致不同的作業模式之間切換偵錯工具的方式實作的服務。