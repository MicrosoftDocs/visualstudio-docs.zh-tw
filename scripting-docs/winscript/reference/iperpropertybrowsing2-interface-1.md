---
title: IPerPropertyBrowsing2 介面 1 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159578"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 介面 1
存取物件所提供的屬性頁中的資訊。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|`GetDisplayString`|傳回文字字串描述指定的屬性。|  
|`MapPropertyToPage`|傳回允許管理指定之屬性的屬性頁 CLSID。|  
|`GetPredefinedStrings`|會傳回計數的字串陣列 (`LPOLESTR`指標) 列出允許的值可以接受指定之的屬性的描述。|  
|`SetPredefinedValue`|將屬性的值設定為預先定義的語彙基元所識別的值 `dwCookie.`|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop.h