---
title: MSBuild 回應檔 | Microsoft Docs
description: 瞭解 MSBuild 回應或 .rsp 檔案、包含 MSBuild.exe 命令列參數的文字檔。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17a4e10864776540c176fd6911917071aa42c656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860863"
---
# <a name="msbuild-response-files"></a>MSBuild 回應檔

回應檔 (*.rsp*) 是包含 *MSBuild.exe* 命令列參數的文字檔。 每個參數可位於單獨一行，或所有參數可位於同一行。 批註行會以 **#** 符號開頭。 **@** 參數是用來將另一個回應檔傳遞至 *MSBuild.exe*。

## <a name="msbuildrsp"></a>MSBuild.rsp

自動回應檔是 *MSBuild.exe* 在建置專案時自動使用的特殊 *.rsp* 檔案。 這個檔案（ *msbuild.exe*）必須與 *MSBuild.exe* 位於相同的目錄中，否則將找不到該檔案。 您可以編輯此檔案以指定 *MSBuild.exe* 的預設命令列參數。 例如，如果您每次建置專案時都使用相同的記錄器，則可以將 **-logger** 參數新增至 *MSBuild.rsp*，*MSBuild.exe* 即會在每次建置專案時使用這個記錄器。

## <a name="directorybuildrsp"></a>Directory.Build.rsp

在 15.6 版和更新版本中，MSBuild 會在專案的父目錄中，搜尋名為 *Directory.Build.rsp* 的檔案。  這有助於原始程式碼儲存機制在命令列建置期間提供預設引數。  它也可用來指定裝載之組建的命令列引數。

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [命令列參考](../msbuild/msbuild-command-line-reference.md)
