---
title: EX_DBGPROP_INFO_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b40ef5c0ceb950873b47033d51555c3ba2fe27a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094506"
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
用來指定`ExtendedDebugPropertyInfo`欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>成員  
 EX_DBGPROP_INFO_ID  
 初始化屬性的識別碼。  
  
 EX_DBGPROP_INFO_NTYPE  
 屬性會初始化型別。  
  
 EX_DBGPROP_INFO_NVALUE  
 初始化屬性的值。  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 初始化`plb`欄位。  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 初始化`pDebugExtProp`欄位包含`IDebugExtendedProperty`介面。  
  
## <a name="see-also"></a>另請參閱  
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)