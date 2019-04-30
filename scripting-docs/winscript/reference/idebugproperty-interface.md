---
title: IDebugProperty 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 963b11a4760fad8086822f13db129fae76467802
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979058"
---
# <a name="idebugproperty-interface"></a>IDebugProperty 介面
用來描述任何階層式實體的屬性進行偵錯具有名稱、 類型和值。 大多數情況下，`IDebugProperty`用來描述運算式評估、 陳述式的評估或註冊評估的結果。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProperty`介面。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|取得`DebugPropertyInfo`，描述這個 `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|取得屬性的擴充的資訊。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|從字串中設定屬性的值。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|列舉屬性的成員。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|取得屬性的父代。|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop.h