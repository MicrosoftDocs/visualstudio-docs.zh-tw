---
title: IEnumDebugErrorBreakpoints2：： Next |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Next
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6cc6e27fc5e6ac5ad380a3168f55dd810fd9dcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199666"
---
# <a name="ienumdebugerrorbreakpoints2next"></a>IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

傳回列舉中的下一組元素。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要取出的元素數目。 也指定陣列的大小上限 `rgelt` 。  
  
 `rgelt`  
 [in，out]要填入的 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 元素陣列。  
  
 `pceltFetched`  
 擴展傳回實際傳回的元素數目 `rgelt` 。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果可以傳回小於所要求的元素數目，則傳回，否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
