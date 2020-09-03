---
title: Debug 封裝 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181299"
---
# <a name="debug-package"></a>偵錯套件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debug 封裝會在 Visual Studio shell 中執行，並處理所有的 UI。 它會取用 Visual Studio 的偵錯工具，並與會話 debug manager (SDM) 進行通訊。  
  
 中斷透過 SDM 傳送的事件將偵錯工具從執行模式切換到中斷模式，並將焦點變更至發生中斷的程式。 Debug 封裝會從事件傳送給它的資訊中追蹤堆疊框架和執行緒。  
  
 Debug 封裝沒有語言或執行時間環境相依性。 不需要執行或修改偵錯工具封裝。  
  
 Debug 封裝是由 vsdebug.dll 所執行。  
  
## <a name="see-also"></a>另請參閱  
 [會話偵錯工具管理員](../../extensibility/debugger/session-debug-manager.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
