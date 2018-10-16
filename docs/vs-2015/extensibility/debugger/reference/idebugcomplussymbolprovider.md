---
title: IDebugComPlusSymbolProvider |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad4fdd53c992e618114d88f78bff105074c71172
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237103"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

代表 COM + 符號提供者特有的 managed 程式碼的方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 雖然沒有適合的運算式評估工具 (EE) 的介面以及要用於偵錯引擎 (DE) 之間沒有區隔，下列方法可能會感興趣 DE 開發人員只： AreSymbolsLoaded，GetAddressesInModuleFromPosition、 GetEntryPoint、 GetFunctionLineOffset、 GetLocalVariableLayout、 IsFunctionStale、 LoadSymbols、 LoadSymbolsFromStream、 ReplaceSymbols、 UnloadSymbols 和 UpdateSymbols。  
  
## <a name="methods"></a>方法  
 上的方法除了[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|決定是否偵錯符號載入指定的模組指定的應用程式網域識別項。|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|從指定的基本類型建立類型。|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|將指定的模組中的文件位置對應的偵錯位址陣列。|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|擷取的型別指定的陣列，指定其偵錯位址的相關資訊。|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|擷取其模組和應用程式定義域的組件名稱。|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|擷取具有指定屬性中指定的程式設計語言實作的類別。|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|擷取與指定的屬性，指定模組中的類別。|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|擷取應用程式進入點。|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|擷取表示指定的行位移的函式內的位址。|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|擷取一組方法的區域變數的配置。|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|傳回與指定的語彙基元指定它的中繼資料物件相關聯的名稱。|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|擷取與指定的父屬性指定模組的偵錯符號。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|擷取以供 unmanaged 程式碼的符號讀取器。|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|擷取至其偵錯位址符號類型。|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|判斷是否在指定的偵錯位址函式會刪除。|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|決定是否在指定的偵錯位址函式會被視為過時。|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|決定是否要隱藏在指定的偵錯工具通訊的程式碼。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|載入記憶體中指定的偵錯符號。|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|載入偵錯符號的資料流。|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|目前的偵錯符號取代指定的資料流中。|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|卸載指定的模組，從記憶體的偵錯符號。|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|更新記憶體中的偵錯符號與指定的資料流。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

