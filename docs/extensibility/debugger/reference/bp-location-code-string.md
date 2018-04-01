---
title: BP_LOCATION_CODE_STRING |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2c49962892cdc0c83d8e3b7ae22ca0c4ee7f13d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
用於設定使用者可以輸入從整合式的開發環境 (IDE) 的字串為基礎的程式碼中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>成員  
 `bstrContext`  
 在程式碼中斷點，通常是方法或函式的名稱，當做呼叫堆疊上看到的內容。  
  
 `bstrCodeExpr`  
 使用者會在輸入描述程式碼中斷點的字串。  
  
## <a name="remarks"></a>備註  
 這個結構是屬於[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構做為聯集的一部分。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)