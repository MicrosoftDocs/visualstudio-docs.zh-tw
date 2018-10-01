---
title: SEEK_START |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7306703d96fd89e3b639de9557c1799e9ca3d00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497436"
---
# <a name="seekstart"></a>SEEK_START
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[SEEK_START](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/seek-start)。  
  
指定要啟動的反組譯碼資料流中搜尋的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>成員  
 SEEK_START_BEGIN  
 搜尋目前文件的開頭開始。  
  
 SEEK_START_END  
 啟動搜尋目前文件的結尾。  
  
 SEEK_START_CURRENT  
 啟動搜尋目前文件目前的位置。  
  
 SEEK_START_CODECONTEXT  
 開始搜尋在目前文件指定的程式碼內容。  
  
 SEEK_START_CODELOCID  
 開始搜尋在指定的程式碼位置識別碼。 透過呼叫所取得的程式碼位置識別項[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)。  
  
## <a name="remarks"></a>備註  
 作為引數[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)

