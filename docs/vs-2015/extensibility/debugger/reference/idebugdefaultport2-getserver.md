---
title: IDebugDefaultPort2：： Teamfoundationserverfactory.getserver |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a74a9e846532b119c5b72495c39226effdc94f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196268"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會取得此埠所在伺服器的介面。  
  
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
 擴展傳回執行 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 介面的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)是由 Visual Studio 所執行，代表埠所在的伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
