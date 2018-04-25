---
title: IDiaStackWalker::getEnumFrames |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a86af24d863982a527a5f3bd2fae58b4dbc6d431
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
擷取堆疊框架的列舉值適用於 x86 平台。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pHelper`  
 [in]協助專家[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)物件。  
  
 `ppEnum`  
 [out]傳回[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)物件，其中包含一份[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要取得任何其他平台上的堆疊框架清單，請呼叫[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)