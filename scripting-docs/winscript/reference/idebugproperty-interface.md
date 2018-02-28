---
title: "IDebugProperty 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>IDebugProperty 介面
用來描述正在進行偵錯任何的實體階層式屬性具有名稱、 類型和值。 大多數情況下，`IDebugProperty`用來描述運算式評估、 陳述式評估或暫存器評估的結果。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProperty`介面。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|取得`DebugPropertyInfo`說明這點，`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|取得屬性擴充的資訊。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|從字串中設定屬性的值。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|列舉屬性的成員。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|取得屬性的父代。|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop.h