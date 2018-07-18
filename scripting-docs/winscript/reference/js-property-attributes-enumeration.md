---
title: JS_PROPERTY_ATTRIBUTES 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733768"
---
# <a name="jspropertyattributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES 列舉
指出屬性 (Property) 的屬性 (Attribute)。  
  
## <a name="syntax"></a>語法  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>成員  
  
|名稱|說明|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|此屬性沒有任何屬性。|  
|`JS_PROPERTY_HAS_CHILDREN`|屬性有子系。|  
|`JS_PROPERTY_FAKE`|此屬性代表假的節點，例如 「 [方法] 」。|  
|`JS_PROPERTY_METHOD`|屬性是一種方法。|  
|`JS_PROPERTY_READONLY`|屬性是唯讀。|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|屬性是原生的 WinRT 物件的指標。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)