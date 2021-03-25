---
title: 比較專案資料夾與原始檔控制存放區 |Microsoft Docs
description: 在原始檔控制外掛程式 API 中，會使用 SccDirQueryInfo 和 SccDirDiff 來完成本機專案資料夾與原始檔控制之間的比較。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b334bb6e1b73dd31060020378e91b74e5af102
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063041"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>本機專案資料夾與原始檔控制存放區的選擇性比較
在原始檔控制外掛程式 API 1.2 中，本機專案資料夾與原始檔控制之間的比較會使用 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 和 [SccDirDiff](../../extensibility/sccdirdiff-function.md)函數來完成。

 在 **方案總管** 中，如果選取資料夾而不是個別檔案，則 **比較版本** 的快捷方式功能表會在原始檔控制外掛程式中叫用新的 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 和 [SccDirDiff](../../extensibility/sccdirdiff-function.md) 。

## <a name="new-capability-flags"></a>新功能旗標
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>新函式
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 您 `SccDirQueryInfo` 可以先呼叫函數， `SccDirDiff` 以判斷工作目錄是否為原始檔控制。 此函式會 `SccDirDiff` 顯示目前本機目錄與對應原始檔控制資料夾之間的差異。 此命令會要求原始檔控制外掛程式顯示目錄的變更清單。 原始檔控制外掛程式會提供自己的 UI 來顯示差異。

> [!NOTE]
> 此函數會使用與 [SccDiff](../../extensibility/sccdiff-function.md)相同的命令旗標。 作為原始檔控制外掛程式提供者，您可以選擇不支援目錄的「快速差異」作業。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
