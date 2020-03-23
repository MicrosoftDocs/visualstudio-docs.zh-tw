---
title: GetOutOfDateItems 工作 | Microsoft Docs
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
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272401"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems 工作

協助程式工作，可讀取舊的 tlog、寫入新的 tlog，並傳回一組不是最新狀態的項目。

## <a name="parameters"></a>參數

下表說明 **GetOutOfDateItems** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**CheckForInterdependencies**|選擇性的 **bool** 參數。|
|**CommandMetadataName**|可選**字串**參數。|
|**DependenciesMetadataName**|可選**字串**參數。|
|**HasInterdependencies**|選擇性的 **bool** 輸出參數。|
|**OutOfDateSources**|選擇性的 **ITaskItem[]** 輸出參數。|
|**OutputsMetadataName**|所需的**字串**參數。|
|**來源**|可選**的 ITaskItem]** 參數。|
|**TLogDirectory**|所需的**字串**參數。|
|**TLogNamePrefix**|所需的**字串**參數。|

## <a name="see-also"></a>另請參閱

[任務引用](../msbuild/msbuild-task-reference.md)