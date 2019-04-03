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
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515424"
---
# <a name="custombuild-task"></a>CustomBuild 工作

包裝 Visual C++ 編譯器工具 (cmd.exe)。

## <a name="parameters"></a>參數

下表描述 **CustomBuild** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**BuildSuffix**|選擇性的 **string** 參數。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**TrackerLogDirectory**|選擇性的 **string** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)