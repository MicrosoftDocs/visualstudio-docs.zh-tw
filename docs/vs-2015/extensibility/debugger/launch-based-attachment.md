---
title: 啟動時附加 |Microsoft Docs
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
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e52e364e49bb38e6be812edec9f5fa5d8f26df0f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488552"
---
# <a name="launch-based-attachment"></a>啟動時附加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[啟動時附加](https://docs.microsoft.com/visualstudio/extensibility/debugger/launch-based-attachment)。  
  
啟動時附加至程式便會自動的。 當裝載程式的處理序由 SDM 啟動時，啟動時附加會遵循的路徑類似於手動附件方法。 如需資訊，請參閱[附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## <a name="the-attaching-process"></a>附加的處理程序  
 主要差異在於下列事件的順序**附加**呼叫，如下所示：  
  
1.  傳送**IDebugEngineCreateEvent2** SDM 事件物件。 如需詳細資訊，請參閱 <<c0> [ 傳送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫`IDebugProgram2::GetProgramId`方法**IDebugProgram2**介面傳遞給**附加**方法。  
  
3.  傳送**IDebugProgramCreateEvent2**通知 SDM 事件物件的本機**IDebugProgram2**以 DE 代表程式建立物件。  
  
4.  傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)事件物件，以通知 SDM 啟動的處理序會建立一個新的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

