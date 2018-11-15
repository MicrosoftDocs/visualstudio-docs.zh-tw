---
title: CONTEXT_COMPARE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a17d0b422b65093721a55d4bf8d632aba271a55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950792"
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
 在相同的函式，做為目標的記憶體範圍中的清單中找到的第一個記憶體內容。  
  
 CONTEXT_SAME_MODULE  
 做為目標的記憶體內容相同的模組清單中找到的第一個記憶體內容。  
  
 CONTEXT_SAME_PROCESS  
 位於相同的程序，做為目標的記憶體內容的清單中找到的第一個記憶體內容。  
  
## <a name="remarks"></a>備註  
 作為引數[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)方法。  
  
 這些值用來尋找符合指定的比較準則的清單中的第一個記憶體內容。 記憶體內容給記憶體內容的清單比較自行針對透過`IDebugMemoryContext2::Compare`方法。 在清單中的比較運算子的第一個記憶體內容`true`再傳回。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)