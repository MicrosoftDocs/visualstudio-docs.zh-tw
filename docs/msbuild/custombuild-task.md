---
title: CustomBuild 工作 | Microsoft Docs
description: 本文描述 msbuild CustomBuild 工作，MSBuild 會使用它來支援自訂 c + + 組建進程。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796546"
---
# <a name="custombuild-task"></a>CustomBuild 工作

包裝 Microsoft c + + 編譯器工具（cmd.exe）。 此類別衍生自 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)，但不會使用檔案追蹤功能來探索檔案相依性。 所有的相依性應該明確指定為 AdditionalDependencies，以確保累加建置運作正常。

## <a name="parameters"></a>參數

下表描述 **CustomBuild** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**BuildSuffix**|選擇性的 **字串** 參數。|
|**來源**|必要的 **ITaskItem []** 參數。|
|**TrackerLogDirectory**|選擇性的 **字串** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
