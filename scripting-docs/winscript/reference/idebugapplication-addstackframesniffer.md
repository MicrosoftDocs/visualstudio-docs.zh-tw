---
title: "IDebugApplication::AddStackFrameSniffer |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89faa6481bd5e5934ae2d3b85a0bade83949633a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
將此應用程式中的堆疊框架的列舉值提供者。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdsfs`  
 [in]堆疊框架列舉值提供者加入至這個應用程式。  
  
 `pdwCookie`  
 [out]用來從應用程式中移除此堆疊框架列舉值提供者的 cookie。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 雖然語言引擎通常會呼叫這個方法來公開其偵錯工具的堆疊框架，可能會公開堆疊框架的其他實體。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer 介面](../../winscript/reference/idebugstackframesniffer-interface.md)