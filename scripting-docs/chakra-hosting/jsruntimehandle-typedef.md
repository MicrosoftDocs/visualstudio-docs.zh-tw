---
title: JsRuntimeHandle Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle Typedef
Chakra 執行階段的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>備註  
 每個 Chakra 執行階段都有自己的獨立執行引擎、JIT 編譯器和記憶體回收堆積。 因此，每個執行階段會與其他執行階段完全隔離。  
  
 執行階段可用於任何執行緒上，但一次只能有一個執行緒呼叫執行階段。  
  
> [!WARNING]
>  JsRuntimeHandle 與 Chakra 裝載應用程式開發介面中的其他物件參考不同，由於它本身即包含記憶體回收堆積，因此不會進行記憶體回收。 執行階段會繼續存在，直到呼叫 JsDisposeRuntime 為止。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)