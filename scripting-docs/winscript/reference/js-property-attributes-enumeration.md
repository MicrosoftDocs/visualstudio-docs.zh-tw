---
title: JS_PROPERTY_ATTRIBUTES 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 27aaadfd1d3ff38e9a0382ff1863b73d2bccc325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539439"
---
# <a name="jspropertyattributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES 列舉
指出屬性 (Property) 的屬性 (Attribute)。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>成員  
  
|名稱|描述|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|屬性沒有任何屬性。|  
|`JS_PROPERTY_HAS_CHILDREN`|屬性具有子系。|  
|`JS_PROPERTY_FAKE`|此屬性代表假的節點，例如 「 [方法] 」。|  
|`JS_PROPERTY_METHOD`|屬性是一種方法。|  
|`JS_PROPERTY_READONLY`|屬性是唯讀。|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|屬性是原生的 WinRT 物件的指標。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)