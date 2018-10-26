---
title: IEnumDebugFields::Clone |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c21aa69b27a7ceeddecc6d95608d86d71045038
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836576"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
這個方法會傳回一份目前的列舉，為個別的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)