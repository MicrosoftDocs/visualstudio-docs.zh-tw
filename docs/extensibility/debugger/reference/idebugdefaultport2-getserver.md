---
title: IDebugDefaultPort2::GetServer |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975c86e0f7674d91b16073c2627414ae1de04081
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841829"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
這個方法會取得的伺服器，此連接埠上的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppServer`  
 [out]傳回物件，實作[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)藉由 Visual Studio，並代表連接埠位於伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)