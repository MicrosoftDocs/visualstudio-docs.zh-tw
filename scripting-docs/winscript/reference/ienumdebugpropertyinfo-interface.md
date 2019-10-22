---
title: IEnumDebugPropertyInfo 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574178"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo 介面
列舉 `DebugPropertyInfo` 結構。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示 `IEnumDebugPropertyInfo` 的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|在列舉序列中，抓取指定數目的 `DebugPropertyInfo` 結構。|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|略過列舉序列中指定數目的 `DebugPropertyInfo` 結構。|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|將列舉序列重設為開頭。|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|建立枚舉器，其中包含與目前列舉值相同的列舉狀態。|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|取得列舉值中 `DebugPropertyInfo` 結構的數目。|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop。h  
  
## <a name="see-also"></a>請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)