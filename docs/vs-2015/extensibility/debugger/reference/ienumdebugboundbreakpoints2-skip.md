---
title: IEnumDebugBoundBreakpoints2::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Skip
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad97a8bf861f780ec1d9bdac4220677a4fe1a7e9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941815"
---
# <a name="ienumdebugboundbreakpoints2skip"></a>IEnumDebugBoundBreakpoints2::Skip
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
 [in]略過的項目數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 會傳回`S_FALSE`如果`celt`大於其餘項目數目，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果`celt`指定的值大於其餘的項目，列舉型別設定為結束和`S_FALSE`會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
