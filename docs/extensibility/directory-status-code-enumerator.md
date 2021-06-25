---
title: 目錄狀態碼列舉值 |Microsoft Docs
description: SccDirStatus 列舉值包含的常數值，可指定原始檔控制系統中的目錄狀態，並由 SccDirQueryInfo 使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a504c6c080c34b4506cf4078b64465a3bd6c7d97
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904226"
---
# <a name="directory-status-code-enumerator"></a>目錄狀態碼列舉值
`SccDirStatus`列舉值包含指定原始檔控制系統中目錄狀態的指定常數值。 此列舉是由 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)所使用。 這是在原始檔控制外掛程式 API 的1.2 版中引進。

## <a name="syntax"></a>語法

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>成員
 無法取得 SCC_DIRSTATUS_INVALID 狀態;請勿依賴它。

 SCC_DIRSTATUS_NOTCONTROLLED 目錄不在原始檔控制之下。

 SCC_DIRSTATUS_CONTROLLED 目錄位於原始檔控制之下。

 對應至此目錄的 SCC_DIRSTATUS_EMPTYPROJ 專案是空的。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
