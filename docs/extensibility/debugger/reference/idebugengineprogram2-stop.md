---
title: "IDebugEngineProgram2::Stop |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::Stop
helpviewer_keywords: IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4004ca92b32e63565a71a3a6971ebb4ae073b9f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
停止執行此程式中的所有執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此程式在多個程式的環境中偵錯時，會呼叫這個方法。 收到停止事件，從某些其他程式時，於這個程式會呼叫這個方法。 這個方法的實作應該是非同步的;也就是說，並非所有的執行緒應該需要這個方法會傳回前，先停止。 這個方法的實作可能會只要呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)於這個程式的方法。  
  
 這個方法的回應以傳送沒有偵錯事件。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)