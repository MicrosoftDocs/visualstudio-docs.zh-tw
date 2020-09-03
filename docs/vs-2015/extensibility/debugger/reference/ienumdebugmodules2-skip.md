---
title: IEnumDebugModules2：： Skip |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Skip
helpviewer_keywords:
- IEnumDebugModules2::Skip
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8716bbbe5233e76ef3902bf9984a9d8f2b69f281
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160983"
---
# <a name="ienumdebugmodules2skip"></a>IEnumDebugModules2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

略過指定的元素數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要略過的元素數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果 `celt` 大於剩餘元素的數目，則傳回，否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果 `celt` 指定的值大於剩餘的元素數目，則列舉會設定為 end，並 `S_FALSE` 傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
