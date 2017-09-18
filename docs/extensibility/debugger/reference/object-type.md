---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "OBJECT_TYPE 列舉型別"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定運算式評估工具中的物件型的別。  
  
## 語法  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Members  
 OBJECT\_TYPE\_BOOLEAN  
 表示物件的布林值。  
  
 OBJECT\_TYPE\_CHAR  
 表示物件是一個字元。  
  
 OBJECT\_TYPE\_I1  
 表示物件是一個位元組帶正負號的整數。  
  
 OBJECT\_TYPE\_U1  
 表示物件是一個位元組不帶正負號的整數。  
  
 OBJECT\_TYPE\_I2  
 表示物件的二位元組帶正負號的整數。  
  
 OBJECT\_TYPE\_U2  
 表示物件的二位元組不帶正負號的整數。  
  
 OBJECT\_TYPE\_I4  
 表示物件的四位元組帶正負號的整數。  
  
 OBJECT\_TYPE\_U4  
 表示物件的四位元組不帶正負號的整數。  
  
 OBJECT\_TYPE\_I8  
 表示物件的八位元組帶正負號的整數。  
  
 OBJECT\_TYPE\_U8  
 表示物件的八位元組不帶正負號的整數。  
  
 OBJECT\_TYPE\_R4  
 表示物件的四位元組浮點數值。  
  
 OBJECT\_TYPE\_R8  
 表示物件的八位元組浮點數值。  
  
 OBJECT\_TYPE\_OBJECT  
 表示物件的物件。  
  
 OBJECT\_TYPE\_NULL  
 表示物件為 NULL。  
  
 OBJECT\_TYPE\_CLASS  
 表示物件是一種類別。  
  
## 備註  
 當做引數傳遞[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)和[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)方法。  
  
## 需求  
 標頭: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)