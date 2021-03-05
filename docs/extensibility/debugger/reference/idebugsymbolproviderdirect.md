---
description: 代表可直接存取中繼資料和核心符號介面的符號提供者。
title: IDebugSymbolProviderDirect |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d60af5be925341e5421badb4c3e6e3dae97903b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149310"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
代表可直接存取中繼資料和核心符號介面的符號提供者。

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|根據指定的 debug 位址，抓取應用程式域識別碼。|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|抓取符號群組中模組的相關資訊。|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|抓取符號提供者為其成員之符號群組的相關資訊。|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|捕獲中繼資料匯入資訊。|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|在指定的 debug 位址抓取方法的相關資訊。|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|捕獲非受控碼的符號讀取器。|

## <a name="remarks"></a>備註
 這個介面可以用來取代大部分其他的符號提供者介面。 它可直接存取中繼資料和 `CorSym` 介面。

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
