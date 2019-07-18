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
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6298a512a1848622bf854d6d9ee9084309a0b4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977108"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName 工作

協助程式工作，可取得 cl 和其他工具的輸出檔案名稱，其允許只指定輸出目錄、指定完整檔案名稱，或不指定任何項目。

## <a name="parameters"></a>參數

下表說明 **GetOutputFileName** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**OutputExtension**|必要的 **string** 參數。|
|**OutputFile**|選擇性的 **string** 輸出參數。|
|**OutputPath**|選擇性的 **string** 參數。|
|**SourceFile**|必要的 **string** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)