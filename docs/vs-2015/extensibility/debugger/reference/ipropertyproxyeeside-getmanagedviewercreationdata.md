---
title: IPropertyProxyEESide::GetManagedViewerCreationData |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5161894875ac683e5a6e49ae623bd6025531006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199527"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取此屬性類型的檢視器的相關資訊，才能具現化該檢視器。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `assemName`  
 [out]傳回保存此物件的組件的名稱。  
  
 `assemBytes`  
 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，其中包含這個物件 （如果不可用的任何位元組，這是 null 值） 的組件位元組。  
  
 `assemPdb`  
 [out]傳回`IEEDataStorage`物件，包含符號儲存這個物件的資訊 （如果不可用的任何符號存放區，這是 null 值）。  
  
 `className`  
 [out]傳回包含此物件的類別名稱。  
  
 `alr`  
 [out]傳回值，以從[ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)列舉，指出組件的位置。  
  
 `replacementOk`  
 [out]傳回非零值 (`TRUE`)，可以變更這個物件的值; 如果零 (`FALSE`) 的物件是否唯讀。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 類型視覺化檢視使用這個方法來具現化受管理的檢視器。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
