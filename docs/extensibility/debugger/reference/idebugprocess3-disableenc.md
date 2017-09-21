---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法明確停用編輯後繼續在此程序 \(和它包含所有的程式\)。  自訂的連接埠提供者應該永遠會傳回`E_NOTIMPL`。  
  
## 語法  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### 參數  
 `reason`  
 \[in\]介於[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
> [!NOTE]
>  自訂的連接埠提供者應該永遠會傳回`E_NOTIMPL`。  
  
## 備註  
 一次編輯和繼續已停用處理程序，可以只是用來重新啟動處理序重新啟用。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)