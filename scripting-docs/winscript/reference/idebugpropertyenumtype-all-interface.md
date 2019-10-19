---
title: IDebugPropertyEnumType_All 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574309"
---
# <a name="idebugpropertyenumtype_all-interface"></a>IDebugPropertyEnumType_All 介面
系統會定義 `IDebugPropertyEnumType` 介面，以便在要求適當的列舉值時，將每個 Iid 當做篩選準則傳遞至 `IDebugProperty::EnumMembers`。  
  
## <a name="syntax"></a>語法  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|傳回描述名稱的文字字串|  
  
 下列介面會繼承自 `IDebugPropertyEnumType_All`，而且沒有任何其他方法。  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)