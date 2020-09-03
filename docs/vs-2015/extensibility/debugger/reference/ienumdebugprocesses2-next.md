---
title: IEnumDebugProcesses2：： Next |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37bf16b49a45b03eee6a1b0abb8af5b719dacff7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179133"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回列舉中的下一組元素。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProcess2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint             celt,  
   IDebugProcess2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。  
  
 `rgelt`  
 [in，out]要填入的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 元素陣列。  
  
 `pceltFetched`  
 擴展傳回實際傳回的元素數目 `rgelt` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
