---
title: 檔案狀態碼列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94bd9ff93872139fc056c4c8bb7a59191616919e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342694"
---
# <a name="file-status-code-enumerator"></a>檔案狀態碼列舉值
`SccStatus`列舉值包含具名的常數值會指定在原始檔控制系統中的檔案的狀態。 這個列舉型別由[SccQueryInfo](../extensibility/sccqueryinfo-function.md)並`POPLISTFUNC`回呼函式 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。

## <a name="syntax"></a>語法

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>成員
 無法取得 SCC_STATUS_INVALID 狀態;請勿依賴它。

 SCC_STATUS_NOTCONTROLLED 檔案不在原始檔控制中。

 SCC_STATUS_CONTROLLED 檔案是在原始檔控制。

 SCC_STATUS_CHECKEDOUT 簽出的本機磁碟上目前的使用者。

 SCC_STATUS_OUTOTHER 檔案是由其他使用者簽出。

 SCC_STATUS_OUTEXCLUSIVE 檔案是以獨佔方式簽出。

 SCC_STATUS_OUTMULTIPLE 檔案是由一個以上的使用者簽出。

 SCC_STATUS_OUTOFDATE 檔案不是最新的。

 已從專案刪除 SCC_STATUS_DELETED 檔案。

 鎖定 SCC_STATUS_LOCKED 檔案;允許任何其他版本。

 SCC_STATUS_MERGED 檔案已合併，但尚未修正/驗證。

 SCC_STATUS_SHARED 檔案會在專案之間共用。

 SCC_STATUS_PINNED 檔案會共用明確的版本。

 SCC_STATUS_MODIFIED 檔案已修改/中斷/違反。

 SCC_STATUS_OUTBYUSER 檔案是由目前的使用者簽出。

 SCC_STATUS_NOMERGE 檔案永遠不會與合併，並不需要儲存 GET 之前。

 SCC_STATUS_RESERVED_1 保留供內部使用。

 SCC_STATUS_RESERVED_2 保留供內部使用。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)