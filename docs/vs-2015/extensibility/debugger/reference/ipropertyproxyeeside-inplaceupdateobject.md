---
title: IPropertyProxyEESide::InPlaceUpdateObject |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945228"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

使用指定的資料物件更新物件的資料，並傳回新的資料物件，表示物件的新資料。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，包含新的資料。  
  
 `dataOut`  
 [out]傳回新`IEEDataStorage`物件，其中包含被取代的資料。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法實際上會更新物件的資料。 在傳回的資料[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件不需要在傳入的資料相同`IEEDataStorage`物件，但傳回的物件必須反映屬性的目前值。  
  
 連入的資料物件通常不會實作由 EE。 不過，這個方法所傳回的物件一律藉由 EE，它可讓 EE 實作`IEEDataStorage`上想要使用任何類別的介面。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)方法會建立內送的資料物件為基礎的資料物件，但不會影響屬性的原始資料。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
