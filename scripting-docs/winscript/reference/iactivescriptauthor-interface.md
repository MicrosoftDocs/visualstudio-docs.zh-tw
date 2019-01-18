---
title: IActiveScriptAuthor 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9d9c2a330ee72c6a843cd42586a09bb1d51e3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346367"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor 介面
表示撰寫服務，包括 IntelliSense 和定序的資訊。  
  
 除了繼承自方法`IUnknown`，則`IActiveScriptAuthor`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|將指令碼撰寫引擎的命名空間中的根層級項目名稱。 A*根層級項目*是可包含屬性和方法，並也可以包含事件來源的物件。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|將程式碼的程式碼片段加入做為子系的根層級`IScriptNode`物件。 在主機中，程式碼片段的完整限定的名稱可以有只有兩個層級。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|將指令碼的命名空間中的型別程式庫。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|傳回完成要求的完成內容的字元集。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|傳回含有指定的屬性程式碼片段。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|傳回類型的程式碼區塊中的資訊和錨點指定的字元位置。 IntelliSense、 全域清單和參數提示，這會提供成員的資訊。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|傳回語言的資訊。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|傳回`IScriptNode`作者的指令碼樹狀結構的根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|傳回的文字屬性的程式碼片段。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|傳回指令碼區塊的文字屬性。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|傳回值，這個值，指出指定的字元是否應該認可陳述式完成的應用程式。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|剖析指令碼文字，將文字加入撰寫指令碼撰寫引擎，並建立`IScriptEntry`物件，對應至指令碼區塊。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|移除`NamedItem`撰寫引擎的指令碼的命名空間中的物件。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|移除指令碼撰寫引擎命名空間中的型別程式庫。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)