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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d6e893dcf289c5060f519523b18b53b701f8055
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748114"
---
# <a name="cppclean-task"></a>CPPClean 工作
刪除 MSBuild 在建立C++專案時所建立的暫存檔案。 刪除組建檔案的程序稱為「清除」。

## <a name="parameters"></a>參數
 下表說明 **CPPClean** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**DeletedFiles**|選擇性的 `ITaskItem[]` 輸出參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 輸出檔案項目的陣列。|
|**DoDelete**|選擇性的 **Boolean** 參數。<br /><br /> 如果為 `true` 則清除暫時的組建檔案。|
|**FilePatternsToDeleteOnClean**|必要的 `String` 參數。<br /><br /> 指定要清除的檔案副檔名清單，以分號分隔。|
|**FilesExcludedFromClean**|選擇性的 `String` 參數。<br /><br /> 指定不要清除的檔案清單，以分號分隔。|
|**FoldersToClean**|必要的 `String` 參數。<br /><br /> 指定要清除的目錄清單，以分號分隔。 您可以指定完整或相對路徑，且路徑可以包含萬用字元符號 (*)。|

## <a name="see-also"></a>請參閱
- [工作參考](../msbuild/msbuild-task-reference.md)