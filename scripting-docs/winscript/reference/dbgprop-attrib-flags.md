---
title: DBGPROP_ATTRIB_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3170e310aa3177e2ca7a1dd81ead02bcc4050114
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572604"
---
# <a name="dbgprop_attrib_flags"></a>DBGPROP_ATTRIB_FLAGS
描述 `IDebugProperty` 的各種屬性。 `DebugPropertyInfo` 結構的成員。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Members  
 DBGPROP_ATTRIB_NO_ATTRIB  
 表示沒有屬性。  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 表示 `DebugPropertyInfo::bstrValue` 中的值無效。  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 表示參考或屬性具有子系。  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 表示值是唯讀值。  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 表示具有公用存取的物件。  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 表示具有私用存取的物件。  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 表示具有保護存取的物件。  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 表示具有最終存取的物件。  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 表示全域儲存體。  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 表示靜態儲存體。  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 表示屬性物件。  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 表示虛擬儲存體。  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 表示物件類型是常數。  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 表示這個位置會同步處理執行緒。  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 表示這個位置會隨永續性儲存體而變更。  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 表示這個位置除了這些預先定義的位元外還具有屬性。  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 表示值是來自函式的傳回值。  
  
## <a name="remarks"></a>備註  
 這些旗標也可用來篩選物件的子系。 其值可與位元 OR 結合。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)