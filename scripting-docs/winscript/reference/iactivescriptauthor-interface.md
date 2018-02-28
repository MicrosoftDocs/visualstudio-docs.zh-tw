---
title: "IActiveScriptAuthor 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor 介面
代表撰寫服務，包括 IntelliSense 和定序的資訊。  
  
 除了繼承自`IUnknown`、`IActiveScriptAuthor`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|將指令碼撰寫引擎的命名空間的根層級項目的名稱。 A*根層級項目*是包含屬性和方法，並也可以包含事件來源的物件。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|將程式碼的程式碼片段加入做為子系的根層級`IScriptNode`物件。 在主機中的程式碼片段的完整限定的名稱可以有只有兩個層級。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|將類型程式庫加入至指令碼的命名空間。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|傳回一組要求的完成內容的完成字元。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|傳回具有指定的屬性的程式碼片段。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|傳回在一段程式碼中，輸入資訊和錨點位置，針對指定的字元。 IntelliSense、 全域清單和參數提示，這會提供成員的資訊。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|傳回語言資訊。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|傳回`IScriptNode`作者的指令碼樹狀結構的根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|傳回的文字屬性的程式碼片段。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|傳回指令碼區塊的文字屬性。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|傳回值，指出指定的字元是否應該認可陳述式完成應用程式。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|剖析指令碼文字、 將文字加入撰寫指令碼撰寫引擎，並建立`IScriptEntry`對應至指令碼區塊的物件。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|移除`NamedItem`撰寫引擎指令碼的命名空間中的物件。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|從指令碼撰寫引擎命名空間中移除類型程式庫。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)