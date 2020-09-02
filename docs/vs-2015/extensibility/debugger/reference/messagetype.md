---
title: MESSAGETYPE |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
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
 指出訊息應該傳送至 [輸出] 視窗。 這與的互斥 `MT_MESSAGEBOX` 。  
  
 MT_MESSAGEBOX  
 指出訊息應該會顯示在訊息方塊中。 這與的互斥 `MT_OUTPUTSTRING` 。  
  
 MT_TYPE_MASK  
 用來隔離訊息目的地的遮罩值。  
  
 MT_REASON_EXCEPTION  
 表示顯示為例外狀況結果的訊息方塊。 這與的互斥 `MT_REASON_TRACEPOINT` 。  
  
 MT_REASON_TRACEPOINT  
 指出因達到追蹤點而顯示訊息方塊。 這對而言是互斥的 `MT_REASON_EXCEPTION` 。  
  
 MT_REASON_MASK  
 用來隔離顯示訊息原因的遮罩值。  
  
## <a name="remarks"></a>備註  
 這些值會從 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) 和 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) 方法傳回。  
  
 其中一個原因值可以使用位來與其中一個輸出目的地值結合 `OR` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
