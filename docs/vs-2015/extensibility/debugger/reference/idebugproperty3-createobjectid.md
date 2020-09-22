---
title: IDebugProperty3：： CreateObjectID |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838836"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

建立這個屬性的唯一識別碼，以確保它在所有其他屬性中都是唯一的。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當會話偵錯工具管理員想要確保在所有其他屬性中唯一識別這個屬性時，會呼叫這個方法。 除非已唯一識別它所處理的屬性，否則 debug engine (DE) 支援此方法。 如果 DE 不支援這個方法，則會傳回 `E_NOTIMPL` 。  
  
 在 `CreateObjectID` 呼叫 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 方法時，會終結以建立的任何唯一識別碼，這也表示需要唯一識別此屬性的結尾。  
  
> [!NOTE]
> 沒有任何方法可以取出這個唯一的識別碼，因此當呼叫方法時，DE 可以執行任何想要的唯一識別碼 `CreateObjectID` 。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
