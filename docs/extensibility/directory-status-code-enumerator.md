---
title: 目錄狀態代碼枚舉器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712150"
---
# <a name="directory-status-code-enumerator"></a>目錄狀態代碼枚舉器
枚`SccDirStatus`舉器包含指定的常量值,用於指定源控制系統中目錄的狀態。 此枚舉由[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)使用。 這在原始程式碼管理外掛程式 API 的版本 1.2 中引入了。

## <a name="syntax"></a>語法

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>成員
 無法獲得SCC_DIRSTATUS_INVALID狀態;不要依賴它。

 SCC_DIRSTATUS_NOTCONTROLLED目錄不受原始程式碼管理。

 SCC_DIRSTATUS_CONTROLLED目錄受原始程式碼管理。

 SCC_DIRSTATUS_EMPTYPROJ與此目錄對應的專案為空。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
