---
title: 介面 （偵錯介面存取 SDK） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5eaf63ac57610e9ebde6703f0b5c15bf9607fdde
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941894"
---
# <a name="interfaces-debug-interface-access-sdk"></a>介面 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

方法會依字母順序列之下的內容，並依照 Vtable 順序的介面上的資料表中每個介面。  
  
## <a name="in-this-section"></a>本節內容  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 可讓您控制 DIA SDK 如何計算偵錯物件的虛擬和相對虛擬位址。  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 起始的存取權的偵錯符號的來源。  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 提供偵錯資料流中記錄的存取權。  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 列舉包含的資料來源中的各種偵錯資料流。  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 列舉各種資料來源中包含的框架資料項目。  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 列舉各種資料來源中包含的插入的來源。  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 列舉各種資料來源中包含的行號。  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 列舉包含的資料來源中的各種區段貢獻。  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 列舉各種資料來源中包含的區段。  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 列舉各種資料來源中包含的原始程式檔。  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 列舉各種可用的堆疊框架。  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 列舉各種資料來源中包含的符號。  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 列舉各種資料來源中包含的符號位址。  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 列舉各種資料來源中包含的資料表。  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 公開 （expose) 堆疊框架的詳細的資料。  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 公開 （expose) 的基底的位置和記憶體位移的模組或映像的詳細資料。  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 存取程式的原始程式碼儲存在 DIA 資料來源中。  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 描述對應到來源檔案行號的位元組的映像文字區塊的程序的存取資訊。  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 DIA 符號尋找程序，因此可以讓使用者介面來報告進度的位置嘗試會收到回呼。  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 DIA 符號尋找程序，讓尋找的程序加諸的限制會收到回呼。  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 可讓您讀取 DIA 屬性集的持續性的屬性。  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 可讓用戶端應用程式提供的可執行檔所指定的檔案位置的位元組。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 可讓用戶端應用程式提供的可執行檔的相對虛擬位址所指定的位元組。  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 描述一節所佔比重的擷取資料，也就是連續的記憶體區塊由所提供的映像所編譯的模組。  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 對應至區段的位址空間資料區段數目。  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 提供偵錯符號的查詢內容。  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 表示原始程式檔。  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 公開的堆疊框架的屬性。  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 提供方法，以執行堆疊查核行程使用 PDB 檔案。  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 會維護引動過程之間的堆疊內容[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 可加速查核堆疊使用程式的偵錯資料庫 (PDB) 檔案。  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 描述符號的執行個體的屬性。  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 列舉 DIA 資料來源資料表。  
  
## <a name="related-sections"></a>相關章節  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 列舉型別和 DIA SDK 的各種介面所使用的結構描述。  
  
 [常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 描述可在 DIA SDK 中的常數。  
  
## <a name="see-also"></a>另請參閱  
 [參考資料](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
