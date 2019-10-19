---
title: IScriptNode 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577509"
---
# <a name="iscriptnode-interface"></a>IScriptNode 介面
執行 `IScriptNode` 介面的物件代表網頁。  
  
 除了繼承自 `IUnknown` 的方法之外，`IScriptNode` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|指出物件是否仍在作用中。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|加入 `IScriptEntry` 的子實例。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|加入程式碼片段做為 `IScriptNode` 的子實例。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|刪除物件樹狀結構。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|傳回節點中位於指定索引處的子系。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|傳回應用程式定義的值，用來將程式碼片段與主機物件產生關聯。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|傳回父項的子清單中物件的索引。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|傳回目前腳本節點所使用的指令碼語言。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|傳回 `IScriptNode` 物件的子節點數目。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|傳回物件的父代 `IScriptNode` 物件。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)