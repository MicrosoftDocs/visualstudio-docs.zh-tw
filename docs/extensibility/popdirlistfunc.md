---
title: POPDIRLISTFUNC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: cb56a3e8f90ed31d051f28fe7cfe99be154d2696
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
This is a callback function given to the [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) function to update a collection of directories and (optionally) file names to find out which are under source control.  
  
 The `POPDIRLISTFUNC` callback should be called only for those directories and file names (in the list given to the `SccPopulateDirList` function) that are actually under source control.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parameters  
 pvCallerData  
 [in] User value given to [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` if the name in `lpDirectoryOrFileName` is a directory; otherwise the name is a file name.  
  
 lpDirectoryOrFileName  
 [in] Full local path to a directory or file name that is under source code control.  
  
## <a name="return-value"></a>Return Value  
 The IDE returns an appropriate error code:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Continue processing.|  
|SCC_I_OPERATIONCANCELED|Stop processing.|  
|SCC_E_xxx|Any appropriate source control error should stop processing.|  
  
## <a name="remarks"></a>Remarks  
 If the `fOptions` parameter of the `SccPopulateDirList` function contains the `SCC_PDL_INCLUDEFILES` flag, then the list will possibly contain file names as well as directory names.  
  
## <a name="see-also"></a>See Also  
 [Callback Functions Implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Error Codes](../extensibility/error-codes.md)
