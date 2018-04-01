---
title: IDebugArrayObject::GetRank |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a3da9ad46a39e0324c71a205b005be61298292f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
取得陣列，也就是維度數目的陣序規範。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwRank`  
 [out]傳回次序。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 使用[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)方法來擷取陣列物件的每個維度大小。  
  
## <a name="see-also"></a>請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)