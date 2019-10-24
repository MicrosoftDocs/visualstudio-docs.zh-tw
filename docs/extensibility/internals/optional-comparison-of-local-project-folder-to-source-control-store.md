---
title: 比較專案資料夾與原始檔控制存放區 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726131"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>本機專案資料夾與原始檔控制存放區的選擇性比較
在原始檔控制外掛程式 API 1.2 中，會使用[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)函式來完成本機專案資料夾和原始檔控制之間的比較。

 在**方案總管**中，如果選取了資料夾而不是個別的檔案，[**比較版本**] 快捷方式功能表會叫用原始檔控制外掛程式中的新[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md) 。

## <a name="new-capability-flags"></a>新增功能旗標
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>新函數
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 @No__t_0 函式會在 `SccDirDiff` 之前呼叫，以判斷工作目錄是否由原始檔控制。 @No__t_0 函式會顯示目前本機目錄與對應原始檔控制資料夾之間的差異。 此命令會要求原始檔控制外掛程式顯示目錄的變更清單。 原始檔控制外掛程式會提供自己的 UI 來顯示差異。

> [!NOTE]
> 此函式會使用與[SccDiff](../../extensibility/sccdiff-function.md)相同的命令旗標。 作為原始檔控制外掛程式提供者，您可以選擇不支援目錄的「快速差異」作業。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)