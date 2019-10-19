---
title: IScriptScriptlet 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571881"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet 介面
執行 `IScriptScriptlet` 介面的物件代表事件處理常式腳本。  
  
 除了繼承自 `IScriptEntry` 的方法之外，`IScriptScriptlet` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|傳回與程式碼片段相關聯的事件名稱。|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|傳回與程式碼片段相關聯的簡單事件名稱。 這是不包含任何空白字元的單字名稱。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|傳回程式碼片段物件主機之完整名稱中的最後一個識別碼。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|設定與程式碼片段相關聯的事件名稱。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|設定與程式碼片段相關聯的簡單事件名稱。 這是不包含任何空白字元的單字名稱。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|設定程式碼片段物件主機之完整名稱中的最後一個識別碼。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)