---
title: "IDebugProcess3::Continue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c112a29d6b936b53aef5be5366f4066a66265e4f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
會繼續執行此程序，從停止的狀態。 會保留任何先前的執行狀態 （例如步驟），並在處理序啟動重新執行。  
  
> [!NOTE]
>  應該使用這個方法，而不是[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表要繼續執行的執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此程序如何多的處理序正在進行偵錯，不論哪個處理程序產生 「 停止 」 事件上呼叫這個方法。 實作必須保留先前的執行狀態 （例如步驟），並繼續執行，就好像它永遠不會具有停止之前完成之前執行。 也就是如果執行緒在此程序正在執行之工作的步驟移轉作業和已停止，因為某些其他處理序已停止，然後`Continue`呼叫，指定執行緒必須完成原始進入作業。  
  
 **警告**不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
