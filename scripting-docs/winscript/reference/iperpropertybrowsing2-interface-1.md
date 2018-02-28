---
title: "IPerPropertyBrowsing2 介面 1 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 介面 1
存取物件所提供的屬性頁中的資訊。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|`GetDisplayString`|傳回文字字串描述指定的屬性。|  
|`MapPropertyToPage`|傳回允許管理指定之屬性的屬性頁 CLSID。|  
|`GetPredefinedStrings`|會傳回計數的字串陣列 (`LPOLESTR`指標) 列出可以接受指定之屬性的允許值的描述。|  
|`SetPredefinedValue`|將屬性的值設定為預先定義的語彙基元所識別的值`dwCookie.`|  
  
## <a name="requirements"></a>需求  
 標頭： dbgprop.h