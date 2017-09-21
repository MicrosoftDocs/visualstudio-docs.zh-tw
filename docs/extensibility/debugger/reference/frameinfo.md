---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "FRAMEINFO 結構"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明堆疊框架。  
  
## 語法  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Members  
 m\_dwValidFields  
 從的旗標組合[FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉型別，指定要填入哪些欄位。  
  
 m\_bstrFuncName  
 函式名稱的堆疊框架相關聯。  
  
 m\_bstrReturnType  
 堆疊框架相關聯的傳回型別。  
  
 m\_bstrArgs  
 堆疊框架相關聯的函式引數。  
  
 m\_bstrLanguage  
 語言功能執行。  
  
 m\_bstrModule  
 堆疊框架相關聯的模組名稱。  
  
 m\_addrMin  
 最小實體的堆疊位址。  
  
 m\_addrMAX  
 最大實體的堆疊位址。  
  
 m\_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件，表示此堆疊框架。  
  
 m\_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件，代表包含此堆疊框架的模組。  
  
 m\_fHasDebugInfo  
 非零值 \(`TRUE`\) 如果偵錯資訊存在於指定的框架。  
  
 m\_fHasDebugInfo  
 非零值 \(`TRUE`\) 如果堆疊框架已經不存在於正確的程式碼與相關聯。  
  
 m\_fHasDebugInfo  
 非零值 \(`TRUE`\) 如果堆疊框架將附註的工作階段偵錯管理員 \(SDM\)。  
  
## 備註  
 這個結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法，會自動填入。  此結構也包含在清單中包含的[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面，反而會傳回從呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)