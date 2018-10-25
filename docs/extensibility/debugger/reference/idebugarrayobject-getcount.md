---
title: IDebugArrayObject::GetCount |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4edfaf7b9ef655473244bdcd18bf6b2c31b8210d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891397"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
取得陣列中的項目數目。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwElements`  
 [out]傳回的計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將所有項目的陣列物件視為一維陣列，即使是多維式陣列物件。 例如，假設陣列`myarray[3][2][6]`，這個方法會傳回在 36`pdwElements`參數。 使用[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法來擷取個別的項目一次。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)