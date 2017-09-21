---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "FIELD_MODIFIERS 列舉型別"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定欄位類型修飾的詞。  
  
## 語法  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Members  
 FIELD\_MOD\_ACCESS\_TYPE  
 表示無法存取該欄位。  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 指示欄位具有公用存取。  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 指示欄位有保護的存取權。  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 指示欄位具有私用存取。  
  
 FIELD\_MOD\_NOMODIFIERS  
 指示欄位具有任何修飾詞。  
  
 FIELD\_MOD\_STATIC  
 表示欄位為靜態。  
  
 FIELD\_MOD\_CONSTANT  
 表示此欄位是常數。  
  
 FIELD\_MOD\_TRANSIENT  
 表示欄位是暫時性的。  
  
 FIELD\_MOD\_VOLATILE  
 表示欄位是變動。  
  
 FIELD\_MOD\_ABSTRACT  
 表示欄位為抽象。  
  
 FIELD\_MOD\_NATIVE  
 表示此欄位是原生。  
  
 FIELD\_MOD\_SYNCHRONIZED  
 表示該欄位已同步處理。  
  
 FIELD\_MOD\_VIRTUAL  
 表示此欄位是虛擬。  
  
 FIELD\_MOD\_INTERFACE  
 指示欄位為介面。  
  
 FIELD\_MOD\_FINAL  
 表示最後一個欄位。  
  
 FIELD\_MOD\_SENTINEL  
 表示此欄位是 sentinel。  
  
 FIELD\_MOD\_INNERCLASS  
 表示此欄位是內部類別。  
  
 FIELD\_TYPE\_OPTIONAL  
 表示欄位是選擇性的。  
  
 FIELD\_MOD\_BYREF  
 表示欄位為參考引數。  這是專為方法引數。  
  
 FIELD\_MOD\_HIDDEN  
 表示此欄位必須隱藏或顯示在另一個內容 ； 例如， [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]的 static 區域變數。  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 表示物件的欄位會指示`IUnknown`介面。  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 指示欄位具有特殊的名稱，例如， `.ctor`的建構函式 \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]只\)。  
  
 FIELD\_MOD\_HIDEBYSIG  
 指示欄位具有`Overloads`套用至它的關鍵字 \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]只\)。  
  
 FIELD\_MOD\_WRITEONLY  
 表示此欄位是唯寫性質。  這個值並不包含在`FIELD_MOD_ALL`，因為這些唯寫屬性的欄位的唯一用途是函式評估。  使用者必須明確地向詢問`FIELD_MOD_WRITEONLY`欄位。  
  
 FIELD\_MOD\_ACCESS\_MASK  
 表示欄位存取遮罩。  
  
 FIELD\_MOD\_MASK  
 表示遮罩的欄位修飾詞。  
  
## 備註  
 用於`dwModifiers`成員的[FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)結構。  
  
 這些值也會傳遞至[EnumFields](../Topic/IDebugContainerField::EnumFields.md)方法，以篩選出特定的欄位。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../Topic/IDebugContainerField::EnumFields.md)