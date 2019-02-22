---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e6679c35452c63009046afb275922188d4fede6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916351"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
終結與這個屬性相關聯，指出呼叫端不會再想要找出此屬性唯一從所有其他屬性的唯一識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果偵錯引擎不需要支援屬性的唯一識別碼 （因為它已經追蹤這些唯一內部），則可以只傳回`E_NOTIMPL`這個方法。  
  
 藉由呼叫會建立唯一的識別碼[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)方法，當呼叫端想要確定此屬性會唯一識別以及所有其他屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)