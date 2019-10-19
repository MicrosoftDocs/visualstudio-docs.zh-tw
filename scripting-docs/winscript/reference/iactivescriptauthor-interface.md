---
title: IActiveScriptAuthor 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576161"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor 介面
代表撰寫服務，包括 IntelliSense 和資訊的定序。  
  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptAuthor` 介面也會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|將根層級專案的名稱加入腳本撰寫引擎的命名空間。 *根層級專案*是可以包含屬性和方法的物件，而且也可以包含事件來源。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|加入程式碼程式碼片段做為根層級 `IScriptNode` 物件的子系。 在主機中，程式碼片段的完整名稱只能有兩個層級。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|將類型程式庫加入至腳本的命名空間。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|傳回要求完成內容的完成字元集合。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|傳回具有指定屬性的程式碼片段。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|傳回程序代碼區塊中指定字元的類型資訊和錨點位置。 這會提供成員 IntelliSense、全域清單和參數提示的相關資訊。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|傳回語言資訊。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|傳回作者腳本樹狀結構的 `IScriptNode` 根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|傳回程式碼片段的文字屬性。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|傳回腳本區塊的文字屬性。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|傳回值，指出指定的字元是否應由應用程式認可語句完成。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|剖析腳本文字、將文字新增至撰寫腳本撰寫引擎，並建立與腳本區塊對應的 `IScriptEntry` 物件。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|從腳本撰寫引擎的命名空間移除 `NamedItem` 物件。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|從腳本撰寫引擎命名空間移除類型程式庫。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)