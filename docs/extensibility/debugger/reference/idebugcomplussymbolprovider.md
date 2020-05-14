---
title: IDebugComPlus符號提供者 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733471"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
表示具有特定於託管代碼的方法的 COM+ 符號提供程式。

## <a name="syntax"></a>語法

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>實施者說明
 儘管對表示式賦值器 (EE) 有用的介面與打算由調試引擎 (DE) 使用的介面之間沒有分離,但以下方法可能僅讓 DE 開發人員感興趣:符號載入、獲取位址、獲取入口點、獲取功能線偏移、獲取本地變數佈局、功能化、載入符號、載入符號、替換符號、卸載符號和更新符號。

## <a name="methods"></a>方法
 除了[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|確定是否為給定應用程式域識別符的指定模組載入調試符號。|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|從指定的基元類型創建類型。|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|將指定模組中的文件位置映射到調試位址陣列。|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|檢索給定其調試位址的指定陣列的類型資訊。|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|檢索給定程式集的模組和應用程式域的程式集的名稱。|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|檢索使用給定程式設計語言實現的指定屬性的類。|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|檢索給定模組中具有指定屬性的類。|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|檢索應用程式入口點。|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|在表示給定行偏移量的函數中檢索位址。|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|檢索一組方法的局部變數的佈局。|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|返回與指定權杖關聯的名稱,給定其元數據物件。|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|使用指定模組的給定父屬性檢索調試符號。|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|檢索由非託管代碼使用的符號讀取器。|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|檢索到給定其調試位址的符號類型。|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|確定是否刪除了指定調試位址上的函數。|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|確定指定調試位址的函數是否被視為過時。|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|確定指定除錯器地址的代碼是否隱藏。|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|在記憶體中載入指定的調試符號。|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|載入給定數據流的調試符號。|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|將當前除錯符號取代為指定資料串流中的除錯符號。|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|從記憶體中卸載指定模組的調試符號。|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|使用指定的數據流更新記憶體中的調試符號。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
