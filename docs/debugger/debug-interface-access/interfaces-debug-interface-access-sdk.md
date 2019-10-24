---
title: 介面（Debug Interface Access SDK） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0aa48ae0d3c3b6b05ea469baea1a1e1aa106667
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738690"
---
# <a name="interfaces-debug-interface-access-sdk"></a>介面 (偵錯介面存取 SDK)
方法會依字母順序列于目錄中的每個介面底下，並以 Vtable 順序列示在介面頁面上。

## <a name="in-this-section"></a>本章節內容

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

可讓您控制 DIA SDK 如何計算 debug 物件的虛擬和相對虛擬位址。

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

起始對調試符號來源的存取。

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

提供對調試資料流程中記錄的存取。

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

列舉資料來源中包含的各種 debug 資料流程。

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

列舉資料來源中包含的各種框架資料元素。

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

列舉資料來源中包含的各種插入來源。

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

列舉資料來源中包含的各種行號。

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

列舉資料來源中包含的各種區段貢獻。

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

列舉資料來源中包含的各種區段。

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

列舉資料來源中包含的各種來源檔案。

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

列舉可用的各種堆疊框架。

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

列舉資料來源中包含的各種符號。

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

依位址列舉資料來源中包含的各種符號。

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

列舉資料來源中包含的各種資料表。

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

公開堆疊框架的詳細資料。

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

公開模組或映射的基底位置和記憶體位移的詳細資料。

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

存取儲存在 DIA 資料來源中的程式原始碼。

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

存取描述從影像文字位元組區塊對應至原始程式檔行號之程式的資訊。

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

從 DIA 符號尋找程式接收回呼，因此可讓使用者介面報告位置嘗試的進度。

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

從 DIA 符號尋找程式接收回呼，允許在尋找進程上加諸限制。

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

可讓您讀取 DIA 屬性集的持續性屬性。

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

可讓用戶端應用程式以檔案位置指定的方式提供可執行檔的位元組。

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

可讓用戶端應用程式提供可執行檔的位元組，如相對虛擬位址所指定。

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

抓取描述區段貢獻的資料，也就是由編譯模組貢獻給影像的連續記憶體區塊。

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

將區段編號的資料對應到位址空間的區段。

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

提供 debug 符號的查詢內容。

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

代表原始檔。

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

公開堆疊框架的屬性。

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

提供使用 PDB 檔案進行堆疊逐步解說的方法。

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

維護[IDiaFrameData：： execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法調用之間的堆疊內容。

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

有助於使用程式 debug 資料庫（PDB）檔案來進行堆疊的逐步解說。

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

描述項號實例的屬性。

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

列舉 DIA 的資料來源資料表。

## <a name="related-sections"></a>相關章節
[列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)

描述 DIA SDK 的各種介面所使用的列舉和結構。

[常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

描述 DIA SDK 中可用的常數。

## <a name="see-also"></a>請參閱

- [參考資料](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)