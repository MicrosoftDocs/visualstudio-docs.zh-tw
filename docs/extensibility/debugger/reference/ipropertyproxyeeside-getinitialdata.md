---
title: IPropertyProxyEESide::GetInitialData |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::GetInitialData
helpviewer_keywords:
- IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72edff9590a198e801e7ae654bbac2aaeea3efc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126369"
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
傳回這個物件的初始資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dataOut`  
 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，其中包含此物件的初始資料。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)