---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得電腦相關表示法的堆疊框架相關聯的實體位址範圍。  
  
## 語法  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### 參數  
 `paddrMin`  
 \[\] out傳回此堆疊框架相關聯的最低實體位址。  
  
 `paddrMax`  
 \[\] out傳回此堆疊框架相關聯的最高的實體位址。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的資訊的工作階段偵錯管理員 \(SDM\) 用於排序堆疊框架。  
  
 它會假設呼叫堆疊會向下，也就是在逐漸較低的記憶體位址中新增新的堆疊框架。  執行階段架構必須提供符合這項假設的實體堆疊範圍。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)