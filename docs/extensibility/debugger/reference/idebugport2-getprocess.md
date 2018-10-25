---
title: IDebugPort2::GetProcess |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4958e296e83e3de0d8c3e41b73c0b30af144d743
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863200"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
取得指定的連接埠上執行的處理序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProcess(   
   AD_PROCESS_ID    ProcessId,  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(   
   AD_PROCESS_ID      ProcessId,  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ProcessId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構，指定的處理序識別碼。  
  
 `ppProcess`  
 [out]傳回[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件代表處理程序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)