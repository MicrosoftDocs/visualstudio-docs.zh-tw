---
title: 將項目資料夾與來源控制記憶體進行比較 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706870"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>本機專案資料夾與原始檔控制存放區的選擇性比較
在原始程式碼管理外掛程式 API 1.2 中,使用函數[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)實現了本地項目資料夾和原始程式碼管理之間的比較。

 在**解決方案資源管理員**中,如果選擇了資料夾而不是單個檔,**則比較版本**快捷選單將在原始程式碼管理外掛程式中呼叫新的[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff。](../../extensibility/sccdirdiff-function.md)

## <a name="new-capability-flags"></a>新功能旗標
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>新函式
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 之前`SccDirQueryInfo``SccDirDiff`調用函數以確定工作目錄是否受原始程式碼管理。 該`SccDirDiff`函數顯示當前本地目錄和相應的原始程式碼管理資料夾之間的差異。 此命令要求原始程式碼管理外掛程式顯示目錄的更改清單。 原始程式碼管理外掛程式提供其自己的 UI 來顯示差異。

> [!NOTE]
> 此函數使用與[SccDiff](../../extensibility/sccdiff-function.md)相同的命令標誌。 作為原始程式碼管理外掛程式提供者,您可以選擇不支援目錄的「快速差異」 操作。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
