---
title: IEnumDebugPropertyInfo Interface | Microsoft Docs
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
ms.openlocfilehash: 736bea847908e3c70d6caf2f8e41af38608f4f23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963425"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo 介面
列舉`DebugPropertyInfo`結構。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugPropertyInfo`。  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|擷取指定的數目的`DebugPropertyInfo`列舉型別序列中的結構。|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|略過指定的數目的`DebugPropertyInfo`列舉型別序列中的結構。|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|將列舉序列重設為開頭。|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|取得數`DebugPropertyInfo`中列舉值的結構。|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop.h  
  
## <a name="see-also"></a>另請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)