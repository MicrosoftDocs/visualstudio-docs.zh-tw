---
title: IDebugSymbol供應商直接 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718910"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
表示直接存取中繼資料和核心符號介面的符號提供程式。

## <a name="syntax"></a>語法

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|檢索給定調試位址的應用程式域識別碼。|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|檢索有關符號組中模塊的資訊。|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|檢索有關符號提供程式是其成員的符號組的資訊。|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|檢索元數據導入資訊。|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|在指定的調試地址檢索有關方法的資訊。|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|檢索非託管代碼的符號讀取器。|

## <a name="remarks"></a>備註
 此介面可用於大多數其他符號提供程式介面。 它提供了對元數據和`CorSym`介面的直接訪問。

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
