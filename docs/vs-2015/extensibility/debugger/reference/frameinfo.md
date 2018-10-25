---
title: FRAMEINFO |Microsoft Docs
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
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5474d85cff58b66e2e9fa7bb8a9507383fd4f0c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938743"
---
# <a name="frameinfo"></a>FRAMEINFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

描述堆疊框架。  
  
## <a name="syntax"></a>語法  
  
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
  
```csharp  
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
  
## <a name="members"></a>成員  
 m_dwValidFields  
 從旗標的組合[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉，指定哪些欄位會填入。  
  
 m_bstrFuncName  
 函式相關聯的名稱與堆疊框架。  
  
 m_bstrReturnType  
 堆疊框架相關聯的傳回型別。  
  
 m_bstrArgs  
 要與堆疊框架相關聯的函式的引數。  
  
 m_bstrLanguage  
 在其中實作該函式語言。  
  
 m_bstrModule  
 堆疊框架相關聯的模組名稱。  
  
 m_addrMin  
 最小實體堆疊位址。  
  
 m_addrMAX  
 最大實體堆疊位址。  
  
 m_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件，代表這個堆疊框架。  
  
 m_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)物件，表示包含此堆疊框架的模組。  
  
 m_fHasDebugInfo  
 非零 (`TRUE`) 如果偵錯資訊存在於指定的範圍內。  
  
 m_fHasDebugInfo  
 非零 (`TRUE`) 的堆疊框架是否已不再有效的程式碼與相關聯。  
  
 m_fHasDebugInfo  
 非零 (`TRUE`) 如果工作階段的偵錯管理員 (SDM) 所標註的堆疊框架。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)来填入的方法。 此結構也會包含在清單中包含[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面，反而會從呼叫傳回[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

