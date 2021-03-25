---
title: IDE 所執行的回呼函式 |Microsoft Docs
description: 瞭解外掛程式可在原始檔控制作業期間于適當時間呼叫的回呼函式，以將資訊傳遞至 IDE。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e2e361551fbe03b7f0ef41b19c5d4136aa50472
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068098"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE 所執行的回呼函數
為了與整合式開發環境整合 (IDE) 盡可能順暢地進行整合，並提供統一的終端使用者體驗，原始檔控制外掛程式可以使用 IDE 所執行的回呼函數。 外掛程式可以在原始檔控制作業期間，于適當的時間呼叫這些函式，以將資訊傳遞至 IDE;然後，IDE 可以將此資訊顯示為其原生 UI 中的內嵌元素。 在此案例中，使用者在此案例中的使用方式不會比外掛程式採用自己的 UI 更少。

 必要的標頭檔是 *scc. h*。 預設位置為 *\Program Files\VSIP 8.0 \ EnvSDK\common\inc \\*。 它也在具有原始檔控制外掛程式範例的 VSIP 資料夾中，位於 *\Program Files\VSIP 8.0 \ MSSCCI \\*。

## <a name="in-this-section"></a>本節內容
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 描述 [SccOpenProject](../extensibility/sccopenproject-function.md) 使用的回呼函式，以透過 IDE 顯示來自原始檔控制外掛程式的訊息。

- [POPLISTFUNC](../extensibility/poplistfunc.md) 描述當 IDE 無法完整存取原始檔控制外掛程式（例如版本控制下的檔案）的完整存取權時， [SccPopulateList](../extensibility/sccpopulatelist-function.md) 所使用的回呼函式。

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 描述 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 作業所使用的回呼函數。

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 描述 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 作業所使用的回呼函數。

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 描述呼叫 [SccSetOption](../extensibility/sccsetoption-function.md) 所設定的回呼函式，此函式可讓原始檔控制外掛程式將名稱變更傳遞回 IDE。

## <a name="related-sections"></a>相關章節
- [SccOpenProject](../extensibility/sccopenproject-function.md) 開啟專案。

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 檢查檔案清單中的目前狀態。 此外，當檔案不 `pfnPopulate` 符合的準則時，也會使用函式來通知呼叫端 `nCommand` 。

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 檢查位於原始檔控制下的專案或專案中的目錄和檔案清單。 每個找到的目錄和檔案名都會傳遞至回呼函式。

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) 檢查檔案清單所做的名稱變更。 每個檔案名都會連同其變更狀態一起傳遞給回呼函式。

- [SccSetOption](../extensibility/sccsetoption-function.md) 設定各種不同的選項。 每個選項的開頭都 `SCC_OPT_xxx` 是，而且有自己的定義值集合。

- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md) 描述原始檔控制外掛程式 SDK 參考區段的內容。
