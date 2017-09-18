---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加至程式的工作階段。  
  
## 語法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### 參數  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件，代表附加偵錯引擎會將傳送至事件的回呼函式。  
  
 `dwReason`  
 \[in\]介於[ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)附加作業理由可以解釋的列舉型別。  
  
 `pSession`  
 \[in\]值，這個值可以唯一識別附加到程式上的工作階段。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  這個方法會傳回`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`已經附加程式。  
  
## 備註  
 包含該程式的連接埠可以使用中的值`pSession`來判斷哪一個工作階段嘗試附加至程式。  比方說，如果連接埠允許附加至處理序中，一次只能有一個偵錯工作階段，該連接埠可以決定是否相同的工作階段附加至處理序中的其他程式。  
  
> [!NOTE]
>  介面傳入的`pSession`視為只以 cookie，該值可唯一識別對這個程式 ； 附加的偵錯工作階段管理員 在提供的介面方法，沒有任何可正常運作。  
  
## 請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)