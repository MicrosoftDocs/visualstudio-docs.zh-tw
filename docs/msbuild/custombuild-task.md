---
title: CustomBuild 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595341"
---
# <a name="custombuild-task"></a>CustomBuild 工作

包裝 Microsoft C++編譯器工具 cmd.exe。 此類別衍生自 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)，但不會使用檔案追蹤功能來探索檔案相依性。 所有的相依性應該明確指定為 AdditionalDependencies，以確保累加建置運作正常。

## <a name="parameters"></a>參數

下表描述 **CustomBuild** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**BuildSuffix**|可選**字串**參數。|
|**來源**|必需**的 ITaskItem]** 參數。|
|**TrackerLogDirectory**|可選**字串**參數。|

## <a name="see-also"></a>另請參閱

[任務引用](../msbuild/msbuild-task-reference.md)
