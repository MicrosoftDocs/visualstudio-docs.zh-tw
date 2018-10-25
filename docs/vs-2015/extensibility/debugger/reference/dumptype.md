---
title: DUMPTYPE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e61e40458241ea1eb4249874bd9e9c26c6082257
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907686"
---
# <a name="dumptype"></a>DUMPTYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定多少程式的狀態 （例如執行中執行緒的堆疊框架和目前的指令位址），傾印。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>成員  
 DUMP_MINIDUMP  
 指定的小、 精簡的傾印。  
  
 DUMP_FULLDUMP  
 指定的大型的完整傾印。  
  
## <a name="remarks"></a>備註  
 作為引數[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

