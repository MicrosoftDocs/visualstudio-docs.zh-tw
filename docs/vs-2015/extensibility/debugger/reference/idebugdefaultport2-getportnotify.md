---
title: IDebugDefaultPort2：： GetPortNotify |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0f5b1faf000ef982e38736b3cd3ea89a1dc2dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196289"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會取得此埠的 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppPortNotify`  
 擴展 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一般來說， `QueryInterface` 方法是在執行 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 介面的物件上呼叫，以取得 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 介面。 不過，在某些情況下，會在不同的物件上執行所需的介面。 這個方法會隱藏這些情況，並 `IDebugPortNotify2` 從最適當的物件傳回介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
