---
title: IEnumCodePaths2::Skip |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37fd0a503519fc3fb1b1ccca1110b04a0332b867
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929669"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
略過指定的元素數目。  
  
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
 如果成功，則傳回`S_OK`。 會傳回`S_FALSE`如果`celt`大於其餘項目數目，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果`celt`指定的值大於其餘的項目，列舉型別設定為結束和`S_FALSE`會傳回。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)