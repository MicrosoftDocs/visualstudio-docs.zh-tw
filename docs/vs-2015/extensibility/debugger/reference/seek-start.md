---
title: SEEK_START |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45e664b153c4d643d8fbe8f1cefb207e0a76e18e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204883"
---
# <a name="seek_start"></a>SEEK_START
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要在反組解碼資料流程中開始搜尋的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>成員  
 SEEK_START_BEGIN  
 在目前檔的開頭開始搜尋。  
  
 SEEK_START_END  
 開始搜尋目前檔的結尾。  
  
 SEEK_START_CURRENT  
 開始搜尋目前檔的目前位置。  
  
 SEEK_START_CODECONTEXT  
 開始搜尋目前檔的指定程式碼內容。  
  
 SEEK_START_CODELOCID  
 開始搜尋指定的程式碼位置識別碼。 藉由呼叫 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)來取得程式碼位置識別碼。  
  
## <a name="remarks"></a>備註  
 以引數的形式傳遞至 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [尋求](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
