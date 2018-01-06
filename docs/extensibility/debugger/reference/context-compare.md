---
title: "CONTEXT_COMPARE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beba9f612024a63f8f302411982442df19e0bbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
指定的準則來比較兩個記憶體內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>成員  
 CONTEXT_EQUAL  
 等於目標記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_LESS_THAN  
 小於目標記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_GREATER_THAN  
 大於目標記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 小於或等於目標記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 大於或等於目標記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_SAME_SCOPE  
 位於相同的範圍內，做為目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
 CONTEXT_SAME_FUNCTION  
 第一個記憶體內容的清單中找到所用的目標記憶體範圍與相同的功能。  
  
 CONTEXT_SAME_MODULE  
 第一個記憶體內容的清單中找到所用的目標記憶體內容相同的模組。  
  
 CONTEXT_SAME_PROCESS  
 第一個記憶體內容的清單中找到所用的目標記憶體內容相同的程序。  
  
## <a name="remarks"></a>備註  
 做為引數傳遞[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)方法。  
  
 這些值可用來尋找符合指定的比較準則的清單中的第一個記憶體內容。 記憶體內容指定的記憶體內容的清單比較本身針對透過`IDebugMemoryContext2::Compare`方法。 比較運算子的清單中的第一個記憶體內容`true`再傳回。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)