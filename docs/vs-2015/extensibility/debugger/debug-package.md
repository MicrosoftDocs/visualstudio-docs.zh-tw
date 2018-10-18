---
title: 偵錯封裝 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61df51b422660a5ea116f136b0d5183e59293a02
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286321"
---
# <a name="debug-package"></a>偵錯套件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯封裝在 Visual Studio shell 中執行，並會處理所有的使用者介面。 它會使用 Visual Studio 偵錯介面，並與工作階段的偵錯管理員 (SDM) 通訊。  
  
 透過在 SDM 傳送 break 事件切換偵錯工具執行模式下從中斷模式，並將焦點變更為在發生中斷的程式。 偵錯封裝會從資訊傳送給它的事件追蹤的堆疊框架和執行緒。  
  
 偵錯封裝有任何語言或執行階段環境相依性。 您不需要實作或修改套件偵錯。  
  
 偵錯封裝是由 vsdebug.dll 實作。  
  
## <a name="see-also"></a>另請參閱  
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)

