---
title: GETNAME_TYPE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17cd40938d177f3ea74af13bd84fcf1b873dd650
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getnametype"></a>GETNAME_TYPE
指定要擷取檔案的名稱類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>成員  
 GN_NAME  
 指定的文件或內容的易記名稱。  
  
 GN_FILENAME  
 指定的文件或內容的完整路徑。  
  
 GN_BASENAME  
 指定的基底檔案名稱，而不是文件或內容的完整路徑。  
  
 GN_MONIKERNAME  
 Moniker 的表單中指定的文件或內容的唯一名稱。  
  
 GN_URL  
 指定的文件或內容的 URL 名稱。  
  
 GN_TITLE  
 如果有的話，請指定文件的標題。  
  
 GN_STARTPAGEURL  
 取得處理程序的起始頁面 URL。  
  
## <a name="remarks"></a>備註  
 這些值會當做參數傳遞給[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)， [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)，和[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法，以指定要傳回名稱的類型。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)