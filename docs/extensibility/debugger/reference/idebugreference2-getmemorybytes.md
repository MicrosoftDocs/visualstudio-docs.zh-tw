---
title: IDebugReference2::GetMemoryBytes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8510e766f7bbace55ee323072cf142a9dd78a759
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
取得記憶體的位元組實際包含參考的值。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppMemoryBytes`  
 [out]傳回[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)可以用來擷取包含參考的值的記憶體的物件。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)