---
title: IEnumDebugFields::Skip |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c2a87f0f03bca4e52e40a7f6a79273f06683aae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123253"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
這個方法會略過指定的項目數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果`celt`其餘項目數目大於; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果`celt`指定的值大於數的其餘項目，列舉型別設定為結束和`S_FALSE`傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)