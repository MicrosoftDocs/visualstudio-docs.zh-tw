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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778133"
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