---
title: "IDebugEngineProgram2::WatchForThreadStep |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3ca2e5eff223a22a3359f6fc4a391d2102f31b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
監看是否正在執行 （或停止觀賞執行） 在給定的執行緒上發生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pOriginatingProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表要逐步執行程式。  
  
 `dwTid`  
 [in]指定要監看之執行緒的識別項。  
  
 `fWatch`  
 [in]非零 (`TRUE`) 表示開始觀賞所識別的執行緒上執行`dwTid`，否則零 (`FALSE`) 表示停止上觀賞執行`dwTid`。  
  
 `dwFrame`  
 [in]指定控制步驟類型的框架索引。 這是當值是零 (0)、 步驟類型是 「 逐步執行 」 和所識別的執行緒時，應該停止程式`dwTid`執行。 當`dwFrame`為非零，步驟類型是 「 不進入 」 和程式在所識別的執行緒時，才應該停止`dwTid`正在執行中的索引是等於或高於堆疊中較高的畫面格`dwFrame`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當工作階段的偵錯管理員 (SDM) 步驟所識別的程式`pOriginatingProgram`參數，它會通知其他所有附加的程式藉由呼叫這個方法。  
  
 這個方法是只適用於逐步執行同一個執行緒。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)