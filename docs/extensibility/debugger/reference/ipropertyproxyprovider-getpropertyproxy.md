---
title: IPropertyProxyProvider::GetPropertyProxy |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 83a4f1e68ff58e61feb1d185626c4d55c16f6589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836485"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
擷取的屬性 proxy 介面做為指定之 proxy 識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwID`  
 [in]所需的屬性 proxy 的識別碼。  
  
 `proxy`  
 [out]傳回[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要支援外部類型視覺化檢視，這個方法通常將呼叫轉送到[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)方法。 請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需有關如何取得 IEEVisualizerService。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)