---
title: 啟用要進行調試的程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155369"
---
# <a name="enabling-a-program-to-be-debugged"></a>啟用要偵錯的程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在您的 debug engine (DE) 可以對程式進行偵錯工具之前，您必須先將它取消或附加至現有的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)  
 討論如何取得埠做為啟用程式進行偵錯工具的第一個步驟。  
  
 [註冊程式](../../extensibility/debugger/registering-the-program.md)  
 說明啟用程式以進行調試的下一個步驟：向埠註冊程式。 註冊之後，就可以透過附加或即時 (JIT) 偵錯工具來偵錯工具。  
  
 [附加至程式](../../extensibility/debugger/attaching-to-the-program.md)  
 說明下一步：將偵錯工具附加至程式。  
  
 [啟動型附加](../../extensibility/debugger/launch-based-attachment.md)  
 描述以啟動為基礎的附加程式，此程式會在 SDM 啟動時自動啟動。  
  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)  
 在建立偵錯工具引擎時，逐步引導您完成所需的事件 (取消) ，並將它附加至程式。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 定義 debug engine (DE) ，並說明透過 DE 介面所執行的服務，以及它們如何讓偵錯工具在不同的操作模式之間轉換。
