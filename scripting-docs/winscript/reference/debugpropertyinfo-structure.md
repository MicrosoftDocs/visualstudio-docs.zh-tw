---
title: DebugPropertyInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640808"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 結構
描述的階層式本質，具有名稱、 類型和值的物件。 它用來描述的本機變數、 參數、 監看變數和運算式，偵錯 屬性，並註冊。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
## <a name="members"></a>成員  
 dwValidFields  
 用來指定哪些欄位會初始化列舉的資料型別。  
  
 bstrName  
 在內容屬性名稱。  
  
 bstrType  
 屬性類型，作為格式化字串。  
  
 bstrValue  
 屬性值，作為格式化字串。  
  
 bstrFullName  
 屬性的完整名稱。  
  
 dwAttrib  
 列舉，指定偵錯屬性的屬性旗標。  
  
 pDebugProp  
 `IDebugProperty`此資訊來描述`DebugPropertyInfo`結構。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)