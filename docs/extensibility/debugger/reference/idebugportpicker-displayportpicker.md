---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

顯示指定的對話方塊，可讓使用者選取一個連接埠。  
  
## 語法  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### 參數  
 `hwndParentDialog`  
 \[in\]父對話方塊的控制代碼。  
  
 `pbstrPortId`  
 \[\] out連接埠識別項的字串。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回值為`S_FALSE` \(或傳回值為`S_OK`與`BSTR`設定為 \[ `NULL`\) 表示使用者已按一下**取消**。  
  
## 請參閱  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)