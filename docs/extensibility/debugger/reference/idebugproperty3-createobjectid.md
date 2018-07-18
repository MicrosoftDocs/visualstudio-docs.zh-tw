---
title: IDebugProperty3::CreateObjectID |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120971"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
建立這個屬性以確保它是唯一在所有其他屬性之間的唯一識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 偵錯工作階段管理員想要確定在所有其他屬性間唯一識別出此屬性時，會呼叫這個方法。 偵錯引擎 (DE) 支援這個方法，除非已經唯一識別它所處理的屬性。 如果 DE 不支援這個方法，它會傳回`E_NOTIMPL`。  
  
 使用任何唯一的識別碼建立`CreateObjectID`時終結[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)呼叫方法時，這也表示需要用來唯一識別這個屬性的結束。  
  
> [!NOTE]
>  沒有任何方法來擷取這個唯一識別碼，因此 DE 可以執行任何它需要的唯一識別碼時`CreateObjectID`方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)