---
title: GetOutputFileName 工作 | Microsoft Docs
description: 使用 MSBuild GetOutputFileName helper 工作來指定 cl.exe 和其他工具的輸出檔案名選項。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436780"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName 工作

協助程式工作，可取得 cl 和其他工具的輸出檔案名稱，其允許只指定輸出目錄、指定完整檔案名稱，或不指定任何項目。

## <a name="parameters"></a>參數

下表說明 **GetOutputFileName** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**OutputExtension**|必要的 **字串** 參數。|
|**OutputFile**|選擇性的 **string** 輸出參數。|
|**OutputPath**|選擇性的 **字串** 參數。|
|**SourceFile**|必要的 **字串** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
