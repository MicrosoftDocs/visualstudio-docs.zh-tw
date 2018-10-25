---
title: IEnumDebugReferenceInfo2::Clone |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugReferenceInfo2::Clone
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Clone
ms.assetid: 49c5a301-a33a-428f-b83b-e734c71af4ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6535c381d88efd92c12cbf57abf1243fbe15d09f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938080"
---
# <a name="ienumdebugreferenceinfo2clone"></a>IEnumDebugReferenceInfo2::Clone
傳回一份目前的列舉，為個別的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone(  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)