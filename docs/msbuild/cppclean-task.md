---
title: CPPClean 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634340"
---
# <a name="cppclean-task"></a>CPPClean 工作

刪除建立 c + + 專案時 MSBuild 所建立的暫存檔案。 刪除組建檔案的程序稱為「清除」**。

## <a name="parameters"></a>參數

 下表說明 **CPPClean** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**DeletedFiles**|選擇性的 `ITaskItem[]` 輸出參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 輸出檔案項目的陣列。|
|**DoDelete**|選擇性的 **布林值** 參數。<br /><br /> 如果為 `true` 則清除暫時的組建檔案。|
|**FilePatternsToDeleteOnClean**|必要的 `String` 參數。<br /><br /> 指定要清除的檔案副檔名清單，以分號分隔。|
|**FilesExcludedFromClean**|選擇性的 `String` 參數。<br /><br /> 指定不要清除的檔案清單，以分號分隔。|
|**FoldersToClean**|必要的 `String` 參數。<br /><br /> 指定要清除的目錄清單，以分號分隔。 您可以指定完整或相對路徑，且路徑可以包含萬用字元符號 (*)。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
