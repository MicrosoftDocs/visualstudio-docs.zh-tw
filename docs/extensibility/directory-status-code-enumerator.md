---
title: 目錄狀態碼列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e62685a1a351c9a5773e18a53316106a18af66a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694656"
---
# <a name="directory-status-code-enumerator"></a>目錄狀態碼列舉值
`SccDirStatus`列舉值包含具名的常數值會指定在原始檔控制系統中的目錄的狀態。 這個列舉型別由[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。 這是在原始檔控制外掛程式 API 1.2 版中引進。

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
 無法取得 SCC_DIRSTATUS_INVALID 狀態;請勿依賴它。

 SCC_DIRSTATUS_NOTCONTROLLED 目錄不是原始檔控制之下。

 SCC_DIRSTATUS_CONTROLLED 目錄是在原始檔控制。

 SCC_DIRSTATUS_EMPTYPROJ 專案對應至這個目錄是空的。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)