---
title: IDebugProgram2::Continue |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4429e4ba9d60dfa8db78ba38257a93b4c14c87e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226222"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

會繼續執行此程式從已停止的狀態。 會保留任何先前的執行狀態 （例如在步驟），並在程式啟動重新執行。  
  
> [!NOTE]
>  這個方法已被取代。 使用[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此方法稱為這個方案，不論幾個程式正在偵錯，或哪些程式所產生的 「 停止 」 事件。 實作必須保留先前的執行狀態 （例如在步驟），並繼續執行，就好像它永遠不會具有停止之前完成其前一次執行。 也就是說，如果此程式中的執行緒所執行工作進入作業，而且已停止，因為某些其他程式停止，，然後才呼叫這個方法，程式必須完成原始不進入函式的作業。  
  
> [!WARNING]
>  不會傳送停止事件或即時 （同步） 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫; 否則為偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

