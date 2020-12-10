---
title: 檔案狀態碼列舉值 |Microsoft Docs
description: SccStatus 列舉值包含常數值，可指定原始檔控制系統中檔案的狀態，並由 SccQueryInfo 和 POPLISTFUNC 使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0093e3a79a5a9caf9846c4b418226568e37828f0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994481"
---
# <a name="file-status-code-enumerator"></a>檔案狀態碼列舉值
`SccStatus`列舉值包含指定原始檔控制系統中檔案狀態的指定常數值。 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)和回呼函式會使用這個列舉 `POPLISTFUNC` (如需詳細資料) ，請參閱[POPLISTFUNC](../extensibility/poplistfunc.md) 。

## <a name="syntax"></a>語法

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>成員
 無法取得 SCC_STATUS_INVALID 狀態;請勿依賴它。

 SCC_STATUS_NOTCONTROLLED 檔案不在原始檔控制之下。

 SCC_STATUS_CONTROLLED 檔案在原始檔控制之下。

 SCC_STATUS_CHECKEDOUT 本機磁片上的目前使用者簽出。

 另一位使用者已簽出 SCC_STATUS_OUTOTHER 檔案。

 以獨佔方式簽出 SCC_STATUS_OUTEXCLUSIVE 的檔案。

 有多個使用者簽出 SCC_STATUS_OUTMULTIPLE 檔案。

 SCC_STATUS_OUTOFDATE 檔案不是最新的。

 已從專案中刪除 SCC_STATUS_DELETED 的檔案。

 SCC_STATUS_LOCKED 檔案已鎖定;不允許其他版本。

 SCC_STATUS_MERGED 檔案已合併，但尚未修正/驗證。

 在專案之間共用 SCC_STATUS_SHARED 檔。

 SCC_STATUS_PINNED 的檔案會與明確的版本共用。

 SCC_STATUS_MODIFIED 檔案已遭修改/中斷/違規。

 目前的使用者已簽出 SCC_STATUS_OUTBYUSER 檔案。

 SCC_STATUS_NOMERGE 的檔案永遠不會與合併，且不需要在 GET 之前儲存。

 SCC_STATUS_RESERVED_1 保留供內部使用。

 SCC_STATUS_RESERVED_2 保留供內部使用。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
