---
title: IEnumDebugModules2：： Next |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25211ac1cbe64dd29bbdc85c4f2674b7e9977851
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191904"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回列舉中的下一組元素。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。  
  
 `rgelt`  
 [in，out]要填入的 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 元素陣列。  
  
 `pceltFetched`  
 擴展傳回實際傳回的元素數目 `rgelt` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
