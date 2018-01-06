---
title: "IDebugDisassemblyStream2::Seek |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2725eb876cf66665c27027dd4d9b250ed7e866e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
讀取的指標在中移動反組譯碼資料流給定的指示，相對於指定的位置數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwSeekStart`  
 [in]中的值[SEEK_START](../../../extensibility/debugger/reference/seek-start.md)列舉，指定相對的位置開始搜尋程序。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表相對於搜尋作業的程式碼內容。 只有當使用這個參數`dwSeekStart`  =  `SEEK_START_CODECONTEXT`; 否則這個參數會被忽略，而且可以是 null 值。  
  
 `uCodeLocationId`  
 [in]搜尋作業是相對於程式碼位置識別項。 如果使用這個參數`dwSeekStart`  =  `SEEK_START_CODELOCID`; 否則這個參數會被忽略，可以設定為 0。 請參閱 < 備註 > 一節的[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)方法的程式碼的位置識別項的描述。  
  
 `iInstructions`  
 [in]如何移動相對於指定的位置數目`dwSeekStart`。 這個值可以是負數向後移動。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`搜尋位置是否可用的指示清單以外的點。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果搜尋到清單的位置開始之前，讀取的位置是設定為清單中的第一個指令。 如果此，請參閱為到位置清單的結尾之後，讀取的位置會設定到最後一個指示清單中。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)