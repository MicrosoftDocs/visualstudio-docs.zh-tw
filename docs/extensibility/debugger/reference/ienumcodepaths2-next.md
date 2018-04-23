---
title: IEnumCodePaths2::Next |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63e13ece4b91721cb391d5f7875c2799e297068b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
列舉中傳回下一個項目的集合。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]若要擷取的項目數目。 也會指定的大小上限`rgelt`陣列。  
  
 `rgelt`  
 [in、 out]陣列[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)要填入的項目。  
  
 `pceltFetched`  
 [out]傳回的項目數中實際傳回`rgelt`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果無法傳回要求的元素數目少於; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)