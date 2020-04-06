---
title: 檔案狀態代碼枚舉器 |微軟文件
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
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711445"
---
# <a name="file-status-code-enumerator"></a>檔案狀態代碼枚舉器
枚`SccStatus`舉器包含指定的常量值,用於指定源控制系統中檔的狀態。 此枚舉由[SccQueryInfo](../extensibility/sccqueryinfo-function.md)和`POPLISTFUNC`回調函數使用(有關詳細資訊,請參閱[POPLISTFUNC)。](../extensibility/poplistfunc.md)

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
 無法獲得SCC_STATUS_INVALID狀態;不要依賴它。

 SCC_STATUS_NOTCONTROLLED檔不受原始程式碼管理。

 SCC_STATUS_CONTROLLED文件處於原始程式碼管理之下。

 SCC_STATUS_CHECKEDOUT本地磁碟上的當前用戶簽出。

 SCC_STATUS_OUTOTHER檔由其他用戶簽出。

 SCC_STATUS_OUTEXCLUSIVE檔被完全簽出。

 SCC_STATUS_OUTMULTIPLE檔由多個用戶簽出。

 SCC_STATUS_OUTOFDATE 該檔不是最新的。

 SCC_STATUS_DELETED檔已從項目中刪除。

 SCC_STATUS_LOCKED文件已鎖定;不允許更多版本。

 SCC_STATUS_MERGED檔已合併但尚未修復/驗證。

 SCC_STATUS_SHARED檔在項目之間共用。

 SCC_STATUS_PINNED檔共享到顯式版本。

 SCC_STATUS_MODIFIED檔已被修改/損壞/違反。

 SCC_STATUS_OUTBYUSER檔由當前用戶簽出。

 SCC_STATUS_NOMERGE文件永遠不能與 GET 合併,也不需要在 GET 之前保存。

 SCC_STATUS_RESERVED_1保留供內部使用。

 SCC_STATUS_RESERVED_2保留供內部使用。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
