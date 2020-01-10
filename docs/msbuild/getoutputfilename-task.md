---
title: GetOutputFileName 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593287"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName 工作

協助程式工作，可取得 cl 和其他工具的輸出檔案名稱，其允許只指定輸出目錄、指定完整檔案名稱，或不指定任何項目。

## <a name="parameters"></a>參數

下表說明 **GetOutputFileName** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**OutputExtension**|必要的 **string** 參數。|
|**OutputFile**|選擇性的 **string** 輸出參數。|
|**OutputPath**|選擇性的 **string** 參數。|
|**SourceFile**|必要的 **string** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
