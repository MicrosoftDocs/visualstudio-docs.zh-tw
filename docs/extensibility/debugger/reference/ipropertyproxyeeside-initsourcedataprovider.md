---
title: "IPropertyProxyEESide::InitSourceDataProvider |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords: IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97aec8a64cfa57bda8b1814fac50851c9cde61e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
初始化此物件的來源資料，並傳回物件，其中包含初始資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dataOut`  
 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法沒有任何內容，才能初始化物件，使它可以傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面上物件的資料。 這可讓檢視及，如果允許，變更類型的視覺化檢視物件的資料。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)