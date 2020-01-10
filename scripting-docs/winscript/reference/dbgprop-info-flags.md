---
title: DBGPROP_INFO_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572588"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
用來指定 `DebugPropertyInfo` 欄位  
  
## <a name="syntax"></a>語法  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Members  
 DBGPROP_INFO_NAME  
 初始化 `bstrName` 欄位。  
  
 DBGPROP_INFO_TYPE  
 初始化 `bstrType` 欄位。  
  
 DBGPROP_INFO_VALUE  
 初始化 `bstrValue` 欄位。  
  
 DBGPROP_INFO_FULLNAME  
 初始化 `bstrFullName` 欄位。  
  
 DBGPROP_INFO_ATTRIBUTES  
 初始化 `dwAttrib` 欄位。  
  
 DBGPROP_INFO_DEBUGPROP  
 初始化包含 `IDebugProperty` 介面的 `pDebugProp` 欄位。  
  
 DBGPROP_INFO_AUTOEXPAND  
 指定值欄位應包含此類型物件的自動擴充值（如果有的話）。  
  
## <a name="see-also"></a>另請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)