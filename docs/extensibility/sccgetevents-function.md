---
description: 此函式會抓取佇列狀態事件。
title: SccGetEvents 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 069e9399a91a39d8005d9137bd19f4032773b24a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220790"
---
# <a name="sccgetevents-function"></a>SccGetEvents 函式
此函式會抓取佇列狀態事件。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 lpFileName

[in，out]原始檔控制外掛程式放置傳回的檔案名 (的緩衝區，) _MAX_PATH 個字元。

 lpStatus

[in，out]傳回狀態碼 (查看可能值) 的檔案 [狀態碼](../extensibility/file-status-code-enumerator.md) 。

 pnEventsRemaining

[in，out]傳回在這個呼叫之後，佇列中剩餘的專案數。 如果這個數位很大，呼叫端可能會決定呼叫 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) ，以一次取得所有資訊。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功取得事件。|
|SCC_E_OPNOTSUPPORTED|不支援此函數。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 在閒置處理期間會呼叫這個函式，以查看原始檔控制下的檔案是否有任何狀態更新。 原始檔控制外掛程式會維護它知道的所有檔案的狀態，而且每當外掛程式記下狀態的變更時，狀態和相關聯的檔案都會儲存在佇列中。 當 `SccGetEvents` 呼叫時，會取出並傳回佇列的最上層專案。 此函式限制為只傳回先前快取的資訊，而且必須有非常快速的 (也就是，不會讀取磁片或要求原始檔控制系統提供狀態) ;否則，IDE 的效能可能會開始降級。

 如果沒有要報告的狀態更新，原始檔控制外掛程式會將空字串儲存在所指向的緩衝區中 `lpFileName` 。 否則，外掛程式會儲存狀態資訊已變更之檔案的完整路徑名稱，並傳回適當的狀態碼 ([檔案 [狀態碼](../extensibility/file-status-code-enumerator.md) ]) 中詳述的其中一個值。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [檔案狀態碼](../extensibility/file-status-code-enumerator.md)
