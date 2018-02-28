---
title: "IScriptNode 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-interface"></a>IScriptNode 介面
物件，用於實作`IScriptNode`介面代表網頁。  
  
 除了繼承自`IUnknown`、`IScriptNode`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|指出物件是否仍在作用中。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|將子執行個體加入`IScriptEntry`。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|將程式碼片段加入作為子執行個體`IScriptNode`。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|刪除物件樹狀結構。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|傳回位於指定索引的節點中的子系。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|傳回應用程式定義的值，用來與主機物件產生關聯的程式碼片段。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|傳回父系的子清單中的物件索引。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|傳回目前的指令碼節點使用的指令碼語言。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|傳回的子節點數目`IScriptNode`物件。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|傳回`IScriptNode`物件，該物件的父系物件。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)