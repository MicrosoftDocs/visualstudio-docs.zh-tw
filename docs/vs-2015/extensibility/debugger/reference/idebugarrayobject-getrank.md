---
title: IDebugArrayObject：： GetRank |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf9700e2c3b29561229999506ed789a2e3d6e52e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423669"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得陣列的順位，也就是維度的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 擴展傳回排名。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 您可以使用 [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) 方法來取出陣列物件的每個維度大小。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
