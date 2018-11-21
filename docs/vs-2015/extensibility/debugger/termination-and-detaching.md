---
title: 終止並中斷連結 |Microsoft Docs
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
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1641a9a44a3f37b07e8192169e7301153881484
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773869"
---
# <a name="termination-and-detaching"></a>終止並中斷連結
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明正常終止。  
  
## <a name="discussion"></a>討論  
 在後[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或是[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)介面持續發生，如果沒有任何中斷點、 例外狀況、 執行階段錯誤或要進行偵錯應用程式中的無限迴圈正在偵錯程式會執行到完成為止。 這是正常終止。  
  
 您必須傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)實作正常終止。 這需要實作[IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

