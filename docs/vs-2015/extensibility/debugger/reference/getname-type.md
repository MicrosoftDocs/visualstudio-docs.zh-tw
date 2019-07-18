---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160131"
---
# <a name="getnametype"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定要擷取檔案的名稱類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_GETNAME_TYPE {   
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
public enum enum_GETNAME_TYPE {   
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
 如果有的話，請指定的文件的標題。  
  
 GN_STARTPAGEURL  
 取得處理程序的起始頁面 URL。  
  
## <a name="remarks"></a>備註  
 這些值會做為參數傳遞[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)， [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)，並[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法，來指定要傳回名稱的類型。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
