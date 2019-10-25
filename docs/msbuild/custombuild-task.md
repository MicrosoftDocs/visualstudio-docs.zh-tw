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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748105"
---
# <a name="custombuild-task"></a>CustomBuild 工作

包裝 Microsoft C++編譯器工具 cmd.exe。 此類別衍生自 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)，但不會使用檔案追蹤功能來探索檔案相依性。 所有的相依性應該明確指定為 AdditionalDependencies，以確保累加建置運作正常。

## <a name="parameters"></a>參數

下表描述 **CustomBuild** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**BuildSuffix**|選擇性的 **string** 參數。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**TrackerLogDirectory**|選擇性的 **string** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
