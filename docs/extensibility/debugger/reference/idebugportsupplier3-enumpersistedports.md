---
title: "IDebugPortSupplier3::EnumPersistedPorts |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords: IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49f76fe661ec718759600771149f5363788d3a85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)