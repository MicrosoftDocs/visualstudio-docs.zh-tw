---
title: "SYMBOL_SEARCH_INFO_FIELDS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 799fe42709a0536dbe8389054da32b29e5791d8c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="symbolsearchinfofields"></a>SYMBOL_SEARCH_INFO_FIELDS
指定要擷取的符號資訊種類。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_SYMBOL_SEARCH_INFO_FIELDS  
{  
   SSIF_NONE                = 0x00000000,  
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001  
};  
  
```  
  
## <a name="members"></a>成員  
 SSIF_NONE  
 表示沒有旗標  
  
 SSIF_VERBOSE_SEARCH_INFO  
 傳回所有的搜尋路徑用來尋找符號  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞為參數，以[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)傳回方法，以判斷資訊數量。  
  
> [!NOTE]
>  目前，只有`SSIF_VERBOSE_SEARCH_INFO`支援，且必須指定為`dwFlags`參數`IDebugModule3::GetSymbolInfo`。 所有其他值會傳回錯誤。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
