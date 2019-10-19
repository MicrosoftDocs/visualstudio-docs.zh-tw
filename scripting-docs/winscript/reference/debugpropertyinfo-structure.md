---
title: DebugPropertyInfo 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575074"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 結構
描述具有名稱、類型和值的階層式本質物件。 它是用來描述本機變數、參數、監看變數和運算式，以及暫存器的 debug 屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Members  
 dwValidFields  
 列舉的資料類型，用來指定要初始化的欄位。  
  
 bstrName  
 內容中的屬性名稱。  
  
 bstrType  
 屬性類型，格式為字串。  
  
 bstrValue  
 屬性值，格式為字串。  
  
 bstrFullName  
 屬性的完整名稱。  
  
 dwAttrib  
 列舉，指定 debug 屬性屬性的旗標。  
  
 pDebugProp  
 此 `DebugPropertyInfo` 結構中的資訊所描述的 `IDebugProperty`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)