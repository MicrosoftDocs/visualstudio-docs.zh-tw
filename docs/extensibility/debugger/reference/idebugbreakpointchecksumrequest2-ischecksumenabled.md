---
title: "IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBreakpointChecksumRequest2::IsChecksumEnabled"
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugBreakpointChecksumRequest2::IsChecksumEnabled
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷是否已啟用這份文件的總和檢查碼。  
  
## 語法  
  
```cpp#  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```c#  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### 參數  
 `pfChecksumEnabled`  
 \[\] out此屬性傳回 TRUE 如果總和檢查碼蟀諉 否則，會傳回 FALSE。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)