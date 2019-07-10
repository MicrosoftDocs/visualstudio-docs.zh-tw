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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587010"
---
# <a name="custombuild-task"></a>CustomBuild 工作

包裝 Visual C++ 編譯器工具 (cmd.exe)。 此類別衍生自 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)，但不會使用檔案追蹤功能來探索檔案相依性。 所有的相依性應該明確指定為 AdditionalDependencies，以確保累加建置運作正常。

## <a name="parameters"></a>參數

下表描述 **CustomBuild** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**BuildSuffix**|選擇性的 **string** 參數。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**TrackerLogDirectory**|選擇性的 **string** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
