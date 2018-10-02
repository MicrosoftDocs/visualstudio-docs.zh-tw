---
title: 終止並中斷連結 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7742ec8ef896006bc00bcbdfcf4961c15acdf746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488743"
---
# <a name="termination-and-detaching"></a>終止並中斷連結
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[終止，並卸離](https://docs.microsoft.com/visualstudio/extensibility/debugger/termination-and-detaching)。  
  
以下說明正常終止。  
  
## <a name="discussion"></a>討論  
 在後[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或是[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)介面持續發生，如果沒有任何中斷點、 例外狀況、 執行階段錯誤或要進行偵錯應用程式中的無限迴圈正在偵錯程式會執行到完成為止。 這是正常終止。  
  
 您必須傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)實作正常終止。 這需要實作[IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

