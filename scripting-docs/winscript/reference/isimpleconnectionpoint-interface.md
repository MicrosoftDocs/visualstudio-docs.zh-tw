---
title: "ISimpleConnectionPoint 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint 介面
提供一個簡單的方式描述和列舉的特定連接點上引發的事件。 此介面也可輕易連結`IDispatch`那些事件的物件。 此介面會實作由處理程序進行偵錯管理員 (PDM)，而且由指令碼引擎。  
  
 這個介面是可從`IDebugHelper::CreateSimpleConnectionPoint`。  
  
 除了繼承自`IUnknown`、`ISimpleConnectionPoint`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|建立簡單的連接點物件與用戶端接收器之間的連接。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|在指定範圍的事件中傳回的 DISPID 和每個事件的名稱。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|傳回此介面上公開的事件數目。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|終止透過先前建立諮詢連接`ISimpleConnectionPoint::Advise`。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)