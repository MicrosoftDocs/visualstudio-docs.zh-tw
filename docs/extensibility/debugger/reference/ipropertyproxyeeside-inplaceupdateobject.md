---
title: IPropertyProxyEESide::InPlaceUpdateObject |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dbfecf353dcdb64e6f576a14413923083e7103eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
使用指定的資料物件更新物件的資料，並傳回新的資料物件，表示物件的新資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，其中包含新的資料。  
  
 `dataOut`  
 [out]傳回新`IEEDataStorage`物件，其中包含被取代的資料。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法實際上會更新物件的資料。 在傳回的資料[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件就不需要會在傳入的資料相同`IEEDataStorage`物件，但傳回的物件必須反映屬性的目前值。  
  
 通常由 EE 不實作內送的資料物件。 不過，這個方法所傳回的物件一律由 EE，它可讓 EE 實作`IEEDataStorage`上想要使用任何類別的介面。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)方法建立根據連入的資料物件的資料物件，但不會影響屬性的原始資料。  
  
## <a name="see-also"></a>請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)