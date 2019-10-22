---
title: IScriptEntry 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575388"
---
# <a name="iscriptentry-interface"></a>IScriptEntry 介面
實作用 `IScriptEntry` 介面的物件代表腳本區塊或函式物件。  
  
 除了繼承自 `IScriptNode` 的方法之外，`IScriptEntry` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|傳回對應至 `IScriptEntry` 腳本區塊、函式區塊或程式碼片段之主體的文字。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|傳回識別 `IScriptEntry` 物件的專案名稱。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|對於代表單一物件的專案（例如函式），會傳回物件的名稱。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|傳回專案的開始位置和長度。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|傳回 `IScriptEntry` 函式物件的類型資訊。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|傳回對應至 `IScriptEntry` 腳本區塊的文字，或包含在 `IScriptScriptlet` 事件處理常式中的原始程式碼。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|設定 `IScriptEntry` 腳本區塊或 `IScriptScriptlet` 程式碼片段主體中的文字。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|設定識別 `IScriptEntry` 物件的專案名稱。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|針對代表單一物件（例如函式）的專案，設定物件的名稱。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|設定 `IScriptEntry` 函式物件的類型資訊。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|設定對應于 `IScriptEntry` 腳本區塊的文字，或包含在 `IScriptScriptlet` 事件處理常式中的原始程式碼。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)