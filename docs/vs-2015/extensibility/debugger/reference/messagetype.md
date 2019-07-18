---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547204"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定訊息類型和原因。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>成員  
 MT_OUTPUTSTRING  
 表示訊息應傳送至輸出視窗。 這是從互斥`MT_MESSAGEBOX`。  
  
 MT_MESSAGEBOX  
 指示訊息應該會顯示訊息方塊。 這是從互斥`MT_OUTPUTSTRING`。  
  
 MT_TYPE_MASK  
 要找出訊息的目的地的遮罩值。  
  
 MT_REASON_EXCEPTION  
 表示在發生例外狀況，正在顯示訊息方塊。 這是從互斥`MT_REASON_TRACEPOINT`。  
  
 MT_REASON_TRACEPOINT  
 表示顯示訊息方塊的結果叫用追蹤點。 這是互斥`MT_REASON_EXCEPTION`。  
  
 MT_REASON_MASK  
 要找出所顯示的訊息的原因的遮罩值。  
  
## <a name="remarks"></a>備註  
 會傳回這些值從[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)並[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)方法。  
  
 其中一個原因值可以結合使用位元的輸出目的地值的其中一個`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
