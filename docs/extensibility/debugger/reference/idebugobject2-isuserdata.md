---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData 方法"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷物件是否表示使用者資料。  
  
## 語法  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### 參數  
 `pfUser`  
 \[\] out傳回非零值 \(`TRUE`\) 如果物件代表使用者資料。 零 \(`FALSE`\) 如果不存在。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 使用者資料是屬於模組指定為 JustMyCode \(標示為使用者程式碼，因此顯示堆疊追蹤中的模組的使用者設定選項\) 的任何物件。  
  
## 請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)