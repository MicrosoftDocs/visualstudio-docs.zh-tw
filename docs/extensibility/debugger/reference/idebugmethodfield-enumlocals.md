---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals 方法"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立所選取之方法的區域變數的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 參數  
 `pAddress`  
 \[in\][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)代表偵錯地址內容或從中取得區域變數的範圍中選取的物件。  
  
 `ppLocals`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示清單中的區域變數。 如果不有任何區域變數，否則傳回 null 值。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或傳回 S\_FALSE，如果不有任何區域變數。  否則，會傳回錯誤碼。  
  
## 備註  
 只有包含特定的偵錯的地址區塊中所定義的變數，才會列舉。  若需要所有的區域變數，包括任何編譯器所產生的區域變數，則呼叫[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)方法。  
  
 一種方法可以包含多個範圍的內容或區塊。  例如，下列方法包含有三種範圍、 兩個內部區塊和方法主體本身。  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件代表`func`方法本身。  呼叫`EnumLocals`方法以[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)設定為 \[ `Inner Scope 1`位址傳回的列舉型別包含`temp1`變數，例如。  
  
## 請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)