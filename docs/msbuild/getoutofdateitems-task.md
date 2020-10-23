---
title: GetOutOfDateItems 工作 | Microsoft Docs
description: 使用 MSBuild GetOutOfDateItems helper 工作，即可讀取和寫入交易記錄 (Tlog) ，並傳回不是最新狀態的專案集合。
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436825"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems 工作

協助程式工作，可讀取舊的 tlog、寫入新的 tlog，並傳回一組不是最新狀態的項目。

## <a name="parameters"></a>參數

下表說明 **GetOutOfDateItems** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**CheckForInterdependencies**|選擇性的 **bool** 參數。|
|**CommandMetadataName**|選擇性的 **字串** 參數。|
|**DependenciesMetadataName**|選擇性的 **字串** 參數。|
|**HasInterdependencies**|選擇性的 **bool** 輸出參數。|
|**OutOfDateSources**|選擇性的 **ITaskItem[]** 輸出參數。|
|**OutputsMetadataName**|必要的 **字串** 參數。|
|**來源**|選擇性的 **ITaskItem []** 參數。|
|**TLogDirectory**|必要的 **字串** 參數。|
|**TLogNamePrefix**|必要的 **字串** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)