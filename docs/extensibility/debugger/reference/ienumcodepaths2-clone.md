---
title: "IEnumCodePaths2::Clone |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2::Clone
helpviewer_keywords: IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff7bc52382b2b9684ae8e3d0d7cf875868ec6e76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
傳回目前的列舉，為個別物件的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone(  
   IEnumCodePaths2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumCodePaths2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]傳回這個列舉型別為個別物件的複本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 列舉的副本會呼叫這個方法只有在有相同的原始狀態。 不過，複製和原始的狀態分開的而且可以個別變更。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)