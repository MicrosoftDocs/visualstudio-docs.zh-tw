---
title: IDebugEngineProgram2::WatchForThreadStep |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944081"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

監看的執行 （或停止執行監看） 指定的執行緒上發生。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示正在逐步執行程式。  
  
 `dwTid`  
 [in]指定要監看之執行緒的識別碼。  
  
 `fWatch`  
 [in]非零 (`TRUE`) 表示開始所識別的執行緒上執行監看`dwTid`，則為零 (`FALSE`) 方法可讓您停止上觀賞執行`dwTid`。  
  
 `dwFrame`  
 [in]指定控制項的步驟類型的畫面格索引。 當這是值為零 (0) 步驟類型 「 逐步執行 」，是每當所識別的執行緒時，應該停止程式`dwTid`執行。 當`dwFrame`為非零，步驟類型是 「 進入 」 和程式應該停止的執行緒識別時，才`dwTid`正在執行中的索引是相等或更高版本，比在堆疊上框架`dwFrame`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當工作階段的偵錯管理員 (SDM) 步驟所識別的程式`pOriginatingProgram`參數，它會通知所有其他附加的程式藉由呼叫這個方法。  
  
 這個方法是僅適用於逐步執行同一個執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
