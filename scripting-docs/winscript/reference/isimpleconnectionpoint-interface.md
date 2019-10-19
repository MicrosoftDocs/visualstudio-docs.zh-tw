---
title: ISimpleConnectionPoint 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571798"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint 介面
提供簡單的方式來描述和列舉在特定連接點上引發的事件。 此介面也可讓您輕鬆地將 `IDispatch` 物件連結至這些事件。 這個介面是由進程 Debug Manager （PDM）所執行，並由腳本引擎所使用。  
  
 此介面可從 `IDebugHelper::CreateSimpleConnectionPoint` 取得。  
  
 除了繼承自 `IUnknown` 的方法之外，`ISimpleConnectionPoint` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|建立簡單連接點物件與用戶端接收之間的連接。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|傳回指定的事件範圍內，每個事件的 DISPID 和名稱。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|傳回此介面上公開的事件數目。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|終止先前透過 `ISimpleConnectionPoint::Advise` 建立的諮詢連接。|  
  
## <a name="see-also"></a>請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)