---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason 列舉型別"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!`代表原因， **編輯後繼續**就無法使用。  
  
## 語法  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### 參數  
 ENCUN\_NONE  
 沒有特定理由，為何無法使用 \[編輯後繼續\]。  
  
 ENCUN\_INTEROP  
 編輯後繼續使用也無法於 InterOp 呼叫。  
  
 ENCUN\_SQLCLR  
 編輯後繼續不使用 SQL 程序呼叫使用通用語言執行階段 \(CLR\)。  
  
 ENCUN\_MINIDUMP  
 編輯後繼續\] 不處理迷你的傾印時。  
  
 ENCUN\_EMBEDDED  
 編輯後繼續\] 時不使用處理內嵌程式碼。  
  
 ENCUN\_ATTACH  
 編輯後繼續\] 無法使用工作階段未附加，因為不啟動者\]、 \[偵錯工具。  
  
 ENCUN\_WIN64  
 編輯後繼續\] 不處理 64 位元視窗程式碼時。  
  
## 備註  
 這個列舉型別僅供內部使用的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。  [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)和[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法實作自訂的通訊埠供應商所應一定會傳回`E_NOTIMPL`。  
  
## 需求  
 標頭: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)