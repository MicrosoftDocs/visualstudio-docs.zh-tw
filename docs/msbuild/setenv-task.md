---
title: SetEnv 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 SetEnv 工作來設定或刪除指定環境變數的值。
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7267e90c2fe3e4617fe2bec8bb177baf42ce37b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048304"
---
# <a name="setenv-task"></a>SetEnv 工作

設定或刪除指定環境變數的值。

## <a name="parameters"></a>參數

 下表說明 **SetEnv** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**名稱**|必要的 **String** 參數。<br /><br /> 環境變數的名稱。|
|**OutputEnvironmentVariable**|選擇性 **字串** 輸出參數。<br /><br /> 包含指派給環境變數 (由 **Name** 參數所指定) 的值。|
|**Prefix**|必要的 `Boolean` 參數。<br /><br /> 如果系統會先將 **Value** 參數的值串連到 **Name** 參數所指定的環境變數值，然後將結果指派給環境變數，則為 `true`。 如果系統只會將 **Value** 參數的值指派給環境變數，則為 `false`。|
|**Target**|選擇性的 **字串** 參數。<br /><br /> 指定儲存環境變數的位置。 指定「使用者」或「電腦」。<br /><br /> 如需詳細資訊，請參閱 [EnvironmentVariableTarget 列舉](xref:System.EnvironmentVariableTarget)。|
|**ReplTest1**|選擇性的 **字串** 參數。<br /><br /> 指派給環境變數 (由 **Name** 參數所指定) 的值。 如果 **Value** 是空的但存在變數，則會刪除變數。 如果變數不存在，即使無法執行此作業也不會發生任何錯誤。<br /><br /> 如需詳細資訊，請參閱 [Environment::SetEnvironmentVariable 方法](xref:System.Environment.SetEnvironmentVariable%2A)。|

## <a name="see-also"></a>請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
