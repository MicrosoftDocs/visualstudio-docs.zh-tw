---
title: "IDebugProgram2::GetMemoryBytes |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetMemoryBytes
helpviewer_keywords: IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 927b0b8433e7a39cd864cce614947d43402037e0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
擷取程式所佔用的記憶體位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppMemoryBytes`  
 [out]傳回[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)程式的記憶體位元組表示的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 記憶體的位元組所表示的[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件可用於記憶體及不含任何程式執行時配置的記憶體中的程式的映像。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)