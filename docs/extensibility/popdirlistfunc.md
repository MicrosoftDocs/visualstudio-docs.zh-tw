---
title: POPDIRLISTFUNC |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44a11e6edc9666fcd7614d467a2c9ffaa86b4365
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
這是提供給回呼函式[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)函式來更新目錄以及 （選擇性） 若要找出哪些是原始檔控制下的檔案名稱的集合。  
  
 `POPDIRLISTFUNC`僅適用於這些目錄和檔案名稱應該會呼叫回呼 (在清單中指定給`SccPopulateDirList`函式)，實際上是在原始檔控制。  
  
## <a name="signature"></a>簽章  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>參數  
 pvCallerData  
 [in]提供給使用者值[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)。  
  
 bFolder  
 [in]`TRUE`如果中的名稱`lpDirectoryOrFileName`為目錄，否則為名稱為檔案名稱。  
  
 lpDirectoryOrFileName  
 [in]完整的本機路徑是在原始程式碼控制之下的目錄或檔案名稱。  
  
## <a name="return-value"></a>傳回值  
 IDE 會傳回適當的錯誤程式碼：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|繼續處理。|  
|SCC_I_OPERATIONCANCELED|停止處理。|  
|SCC_E_xxx|適當的原始檔控制的任何錯誤，應該停止處理。|  
  
## <a name="remarks"></a>備註  
 如果`fOptions`參數`SccPopulateDirList`函式包含`SCC_PDL_INCLUDEFILES`旗標，清單可能包含檔案名稱，以及目錄名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [錯誤碼](../extensibility/error-codes.md)