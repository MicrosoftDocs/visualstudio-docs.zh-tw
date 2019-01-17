---
title: IScriptScriptlet Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a3b7c4af7769a1a2851e9be4e2639a324a3c06fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345912"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet 介面
物件，實作`IScriptScriptlet`介面代表事件處理常式指令碼。  
  
 除了繼承自方法`IScriptEntry`，則`IScriptScriptlet`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|傳回與 scriptlet 相關聯之事件的名稱。|  
|[IScriptScriptlet::GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|傳回與 scriptlet 相關聯的簡單事件名稱。 這是不包含任何空白字元的單一字詞名稱。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|傳回最後一個識別項中的程式碼片段物件主控件的完整名稱。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|設定與 scriptlet 相關聯之事件的名稱。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|設定與程式碼片段相關聯的簡單事件名稱。 這是不包含任何空白字元的單一字詞名稱。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|設定程式碼片段物件主機的完整名稱的最後一個識別項。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)