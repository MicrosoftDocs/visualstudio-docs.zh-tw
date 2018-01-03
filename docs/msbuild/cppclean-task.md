---
title: "CPPClean 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92ce404301b2eb2b631969db70fa1dce3febb72b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cppclean-task"></a>CPPClean 工作
刪除在建置 Visual C++ 專案時由 MSBuild 所建立的暫存檔。 刪除組建檔案的程序稱為「清除」。  
  
## <a name="parameters"></a>參數  
 下表說明 **CPPClean** 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|**DeletedFiles**|選擇性的 `ITaskItem[]` 輸出參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 輸出檔案項目的陣列。|  
|**DoDelete**|選擇性的 **Boolean** 參數。<br /><br /> 如果為 `true` 則清除暫時的組建檔案。|  
|**FilePatternsToDeleteOnClean**|必要的 `String` 參數。<br /><br /> 指定要清除的檔案副檔名清單，以分號分隔。|  
|**FilesExcludedFromClean**|選擇性的 `String` 參數。<br /><br /> 指定不要清除的檔案清單，以分號分隔。|  
|**FoldersToClean**|必要的 `String` 參數。<br /><br /> 指定要清除的目錄清單，以分號分隔。 您可以指定完整或相對路徑，且路徑可以包含萬用字元符號 (**\***)。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)