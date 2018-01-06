---
title: "介面 （偵錯介面存取 SDK） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e128aa0a4cbb30106981b152252ff308e21669b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interfaces-debug-interface-access-sdk"></a>介面 (偵錯介面存取 SDK)
方法依字母順序列在每個介面，在該資料表的內容，並依照 Vtable 順序的介面上。  
  
## <a name="in-this-section"></a>本節內容  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 可控制 DIA SDK 會以偵錯物件的虛擬和相對虛擬位址的計算。  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 啟始的存取權的偵錯符號的來源。  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 提供偵錯資料流中記錄的存取。  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 列舉各種資料來源中所包含的偵錯資料流。  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 列舉各種資料來源中所包含的框架資料項目。  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 列舉各種資料來源中所包含的插入的來源。  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 列舉各種資料來源中所包含的行號。  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 列舉各種資料來源中所包含的區段比重。  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 列舉各種資料來源中所包含的區段。  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 列舉各種資料來源中所包含的原始程式檔。  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 列舉各種可用的堆疊框架。  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 列舉各種資料來源中所包含的符號。  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 列舉各種資料來源中所包含的符號的位址。  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 列舉各種資料來源中所包含的資料表。  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 公開堆疊框架的詳細資料。  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 公開的基底的位置和記憶體位移之模組的映像的詳細資料。  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 存取程式的原始程式碼儲存在 DIA 資料來源。  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 存取描述對應到原始程式檔行號位元組的影像文字區塊的程序的資訊。  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 DIA 符號找出程序，因此可以讓使用者介面，以報告進度的位置嘗試從接收回呼。  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 從允許的限制，以可加諸於尋找處理程序，找出程序 DIA 符號接收回呼。  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 可讓您讀取 DIA 屬性集的持續性屬性。  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 可讓用戶端應用程式提供的可執行檔所指定的檔案位置的位元組。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 可讓用戶端應用程式提供的可執行檔的相對虛擬位址所指定的位元組。  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 描述區段比重的擷取資料，也就是連續的記憶體區塊至映像所提供的編譯模組。  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 對應至區段的位址空間區段的數字資料。  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 提供偵錯符號的查詢內容。  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 表示原始程式檔。  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 公開堆疊框架的屬性。  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 提供方法，以執行堆疊查核行程使用 PDB 檔案。  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 會維護的引動過程之間的堆疊內容[idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md)方法。  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 可加速，查核堆疊使用程式的偵錯資料庫 (PDB) 檔。  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 描述符號的執行個體的屬性。  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 列舉 DIA 資料來源資料表。  
  
## <a name="related-sections"></a>相關章節  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 列舉型別和 DIA SDK 各種介面所使用的結構描述。  
  
 [常數 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 描述可在 DIA SDK 中的常數。  
  
## <a name="see-also"></a>請參閱  
 [參考資料](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)