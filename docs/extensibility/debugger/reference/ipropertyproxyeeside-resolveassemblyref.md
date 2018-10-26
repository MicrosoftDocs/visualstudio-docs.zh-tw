---
title: IPropertyProxyEESide::ResolveAssemblyRef |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7711d185e92b0cc8a29070aa78a4acff835df33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846937"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
判斷指定的 managed 組件參考的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `assemName`  
 [in]要解析的組件的名稱。  
  
 `assemBytes`  
 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，其中包含與參考相關聯的組件位元組。  
  
 `assemPdb`  
 [out]傳回`IEEDataStorage`物件，包含符號儲存與這個參考相關聯的資料。  
  
 `assemLocation`  
 [out]傳回此參考的路徑位置。  
  
 `alr`  
 [out]傳回值，以從[ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)列舉，指出此參考的組件的位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 自訂運算式評估工具通常不實作這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)