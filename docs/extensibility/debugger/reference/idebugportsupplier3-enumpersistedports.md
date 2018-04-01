---
title: IDebugPortSupplier3::EnumPersistedPorts |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3d35f3b337183bf6498f64a05534e40e02420ac4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
這個方法會擷取物件，讓保存的連接埠清單的列舉型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `PortNames`  
 [in]A [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)結構，其中包含以尋找並傳回在保存的連接埠之間的連接埠名稱的清單。 只有這些保存連接埠與這些名稱將會傳回。  
  
 `ppEnum`  
 [out]物件，用於實作[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 連接埠供應商會具現化，並儲存連接埠供應商時終結時，會載入保存的連接埠。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)