---
title: MESSAGETYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa09d938e0e7c3853431369c7e0634242df2ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="messagetype"></a>訊息類型
指定訊息類型和原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_MESSAGETYPE {   
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
public enum enum_MESSAGETYPE {   
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
 指示訊息應該會顯示在訊息方塊。 這是從互斥`MT_OUTPUTSTRING`。  
  
 MT_TYPE_MASK  
 若要找出訊息的目的地遮罩值。  
  
 MT_REASON_EXCEPTION  
 表示在發生例外狀況，正在顯示訊息方塊。 這是從互斥`MT_REASON_TRACEPOINT`。  
  
 MT_REASON_TRACEPOINT  
 表示叫用追蹤點的結果，正在顯示訊息方塊。 這是互斥`MT_REASON_EXCEPTION`。  
  
 MT_REASON_MASK  
 若要找出要顯示的訊息的原因遮罩值。  
  
## <a name="remarks"></a>備註  
 這些值會傳回從[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)和[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)方法。  
  
 其中一個原因值可以與一個輸出目的地值使用位元結合`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)