---
title: IDebugHelper 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148056"
---
# <a name="idebughelper-interface"></a>IDebugHelper 介面
作為物件瀏覽器和簡單的連接點的處理站。 處理序偵錯管理員 (PDM) 會實作這個介面，由指令碼引擎。  
  
 除了繼承自方法`IUnknown`，則`IDebugHelper`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|傳回包裝 VARIANT 屬性瀏覽器。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|傳回包裝 VARIANT，並允許 VARIANT 值或 VARTYPE 類型的自訂轉換成字串的屬性瀏覽器。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|傳回包裝的事件介面指定`IDispatch`物件。|