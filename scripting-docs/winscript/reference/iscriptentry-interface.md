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
ms.openlocfilehash: 0dc50a6aa5cf032827feac6b483b141b79f60e77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787720"
---
# <a name="iscriptentry-interface"></a>IScriptEntry 介面
物件，實作`IScriptEntry`介面代表指令碼區塊或函式物件。  
  
 除了繼承自方法`IScriptNode`，則`IScriptEntry`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|傳回對應的文字本文`IScriptEntry`指令碼區塊、 函式區塊或程式碼片段。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|傳回項目名稱可識別`IScriptEntry`物件。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|代表單一物件 （例如函式） 的項目，傳回物件的名稱。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|傳回的起始位置和長度的項目。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|傳回的型別資訊`IScriptEntry`函式物件。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|傳回對應至文字`IScriptEntry`指令碼區塊或包含在原始碼`IScriptScriptlet`事件處理常式。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|設定的主體中的文字`IScriptEntry`指令碼區塊或`IScriptScriptlet`程式碼片段。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|設定項目名稱可識別`IScriptEntry`物件。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|代表單一物件 （例如函式） 的項目，設定物件的名稱。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|設定類型資訊`IScriptEntry`函式物件。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|設定對應至文字`IScriptEntry`指令碼區塊或包含在原始碼`IScriptScriptlet`事件處理常式。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)