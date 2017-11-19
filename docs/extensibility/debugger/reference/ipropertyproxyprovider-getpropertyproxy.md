---
title: "IPropertyProxyProvider::GetPropertyProxy |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords: IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bd09c7f0490d70b969bf9def9870a3a33aac551
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
擷取屬性 proxy 介面的指定之 proxy 識別碼  
  
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
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要支援外部類型視覺化檢視，這個方法通常會將轉送呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)方法。 請參閱[Visualizing 和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需如何取得 IEEVisualizerService 詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)