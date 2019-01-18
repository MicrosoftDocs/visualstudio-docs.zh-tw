---
title: IPerPropertyBrowsing2 介面 1 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344019"
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