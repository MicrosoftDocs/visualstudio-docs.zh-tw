---
title: 'IDebugArrayObject:: GetCount |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35cce37afc389501386ffec7b75b934e7933bc98
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68197797"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得陣列中的元素計數。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwElements`  
 脫銷傳回計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功, 會傳回 S_OK;否則, 會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會將陣列物件的所有元素視為一維陣列, 即使陣列物件是多維度的。 例如, 指定陣列`myarray[3][2][6]`時, 這個方法會`pdwElements`在參數中傳回36。 您可以使用[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法, 一次抓取一個個別元素。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
