---
title: IDebugDisassemblyStream2::Seek |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a545de68b2483a2b924aa0b4a205a8a227a35007
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911651"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

反組譯碼資料流指定數目的相對於指定位置的指示中移動讀取的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]值，以從[SEEK_START](../../../extensibility/debugger/reference/seek-start.md)列舉，指定 開始搜尋程序的相對位置。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，表示相對於搜尋作業的程式碼內容。 使用這個參數才`dwSeekStart`  =  `SEEK_START_CODECONTEXT`，否則會忽略此參數，而且可以是 null 的值。  
  
 `uCodeLocationId`  
 [in]搜尋作業的相對之程式碼位置識別碼。 如果使用這個參數`dwSeekStart`  =  `SEEK_START_CODELOCID`，否則會忽略這個參數，而且可以設定為 0。 請參閱 < 備註 > 一節[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)方法的程式碼的位置識別項的描述。  
  
 `iInstructions`  
 [in]將相對於位置中指定的指令數目`dwSeekStart`。 這個值可以是負數以向後移動。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果搜尋位置是要提供的指示清單以外的點。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果搜尋到清單的開頭之前的位置，會將讀取的位置設在清單中的第一個指令。 時，請參閱至位置清單的結尾之後，讀取的位置設定的最後一個指示清單中。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

