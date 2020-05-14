---
title: SccGet事件功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700811"
---
# <a name="sccgetevents-function"></a>SccGet 事件功能
此函數檢索排隊狀態事件。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 lpFile 名稱

[進出]緩衝區,其中原始程式碼管理外掛程式放置返回的檔名(最多_MAX_PATH個字元)。

 lp狀態

[進出]返回狀態代碼(有關可能的值,請參閱[文件狀態代碼](../extensibility/file-status-code-enumerator.md))。

 pn 事件剩餘

[進出]返回此調用後佇列中留下的條目數。 如果此號碼很大,呼叫者可能會決定呼叫[SccQueryInfo](../extensibility/sccqueryinfo-function.md)以一次獲取所有資訊。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|使事件成功。|
|SCC_E_OPNOTSUPPORTED|不支援此函數。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 在空閒處理期間調用此功能,以查看源控制下的檔是否有任何狀態更新。 原始程式碼管理外掛程式維護它所知道的所有檔案的狀態,每當外掛程式注意到狀態更改時,狀態和關聯的檔都存儲在佇列中。 調用`SccGetEvents`時,將檢索並返回佇列的頂部元素。 此函數受約束僅返回以前緩存的資訊,並且必須有一個非常快速的周轉(即,不讀取磁碟或詢問原始程式碼管理系統的狀態);否則,IDE 的性能可能會開始下降。

 如果沒有要報告的狀態更新,原始程式碼管理外掛程式將空字串存儲在指向`lpFileName`的緩衝區中。 否則,外掛程式將儲存狀態資訊已更改的檔的完整路徑名稱,並返回相應的狀態代碼([檔案狀態代碼](../extensibility/file-status-code-enumerator.md)中詳述的值之一)。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [檔案狀態代碼](../extensibility/file-status-code-enumerator.md)
