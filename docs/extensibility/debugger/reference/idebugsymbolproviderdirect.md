---
description: 代表可直接存取中繼資料和核心符號介面的符號提供者。
title: IDebugSymbolProviderDirect |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cce774ff6c3ca3e1037a4a61f5c8b4f892aa1c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053148"
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
