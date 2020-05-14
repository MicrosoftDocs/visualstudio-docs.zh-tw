---
title: IDE 實現的回調功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739901"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE 實作的回檔
為了使與整合式開發環境 (IDE) 的整合盡可能無縫,並提供統一的最終使用者體驗,原始程式碼管理外掛程式可以使用 IDE 實現的回調功能。 外掛程式可以在原始程式碼管理操作期間的適當時間調用這些函數,以將資訊傳遞給 IDE;然後,IDE 可以將其本地 UI 中的嵌入元素顯示此資訊。 與外掛程式使用其自己的 UI 相比,使用者在此方案中具有較少碎片化的體驗。

 需要的標頭檔是*scc.h*。 預設位置是 *[程式檔案]VSIP 8.0\EnvSDK_common_inc\\*。 它還在 VSIP 資料夾中,該資料夾在 *[程式檔]VSIP\\8.0_MSSCCI*處具有原始程式碼管理外掛程式示例。

## <a name="in-this-section"></a>本節內容
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)描述[SccOpenProject](../extensibility/sccopenproject-function.md)用於透過 IDE 顯示來自原始碼管理外掛程式的消息的回調功能。

- [POPLISTFUNC](../extensibility/poplistfunc.md)描述[SccPopulateList](../extensibility/sccpopulatelist-function.md)在 IDE 無法完全存取僅對原始程式碼管理外掛程式可用的資訊(如版本控制下的檔案的完整清單)時使用的回調功能。

- [查詢變更](../extensibility/querychangesfunc.md)描述[SccQuery 更改](../extensibility/sccquerychanges-function.md)操作使用的回調功能。

- [波普迪利斯芬奇](../extensibility/popdirlistfunc.md)描述[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)操作使用的回調函數。

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)描述對[SccSetOption](../extensibility/sccsetoption-function.md)的呼叫設定的回調功能,該調用使原始程式碼管理外掛程式能夠將名稱更改傳回 IDE。

## <a name="related-sections"></a>相關章節
- [SccOpen專案](../extensibility/sccopenproject-function.md)打開專案。

- [Scc填充清單](../extensibility/sccpopulatelist-function.md)檢查檔案清單的目前狀態。 此外,當檔與`pfnPopulate`的條件`nCommand`不匹配時,使用函數通知調用方。

- [SccpopulateDirlist](../extensibility/sccpopulatedirlist-function.md)檢查受原始碼管理的項目或專案中的目錄和檔案的清單。 找到的每個目錄和檔名都傳遞給回調函數。

- [SccQuery 變更](../extensibility/sccquerychanges-function.md)檢查對檔案清單所做的名稱更改。 每個檔名都傳遞給回調函數及其更改狀態。

- [SccSetOption](../extensibility/sccsetoption-function.md)設置各種選項。 每個選項都從`SCC_OPT_xxx`並有自己的定義值集開始。

- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)描述原始程式碼管理外掛程式 SDK 的參考部分的內容。
