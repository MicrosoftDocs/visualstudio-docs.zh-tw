---
title: "偵錯封裝 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2cbb124dcb2d2d7a0bbcba1bc57eb3c704dd770
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debug-package"></a>偵錯封裝
偵錯封裝在 Visual Studio shell 中執行，並處理所有的使用者介面。 它會使用 Visual Studio 偵錯介面和通訊工作階段的偵錯管理員 (SDM)。  
  
 中斷事件傳送到 SDM 切換偵錯工具從執行模式中斷模式，並將焦點變更為在發生中斷的程式。 偵錯封裝會從資訊傳送給它的事件追蹤的堆疊框架和執行緒。  
  
 偵錯封裝有任何語言或執行階段環境的相依性。 您不需要實作或修改偵錯封裝。  
  
 偵錯封裝是由 vsdebug.dll 實作。  
  
## <a name="see-also"></a>請參閱  
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)