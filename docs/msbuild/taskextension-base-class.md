---
title: TaskExtension 基底類別 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3dc771f16c7077549ba06d5cdda422319554d40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631701"
---
# <a name="taskextension-base-class"></a>TaskExtension 基底類別

許多工作繼承自 <xref:Microsoft.Build.Tasks.TaskExtension> 類別，而該類別本身繼承自 <xref:Microsoft.Build.Utilities.Task> 類別。 此繼承鏈結將數個參數加入至從它們衍生的工作。 本文件會列出這些參數。

## <a name="parameters"></a>參數

 下表說明基底類別的參數。

|參數|描述|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine> 參數。<br /><br /> 指定工作可以使用的建置引擎介面。 建置引擎會自動設定這個參數，以允許工作回呼至它。|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine2> 參數。<br /><br /> 指定工作可以使用的建置引擎介面。 建置引擎會自動設定這個參數，以允許工作回呼至它。<br /><br /> 這是方便的屬性，讓工作作者繼承自這個類別，不需要將值從 `IBuildEngine` 轉型到 `IBuildEngine2`。|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|選擇性的 <xref:Microsoft.Build.Framework.IBuildEngine3> 參數。<br /><br /> 指定主機提供的建置引擎介面。|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|選擇性的 <xref:Microsoft.Build.Framework.ITaskHost> 參數。<br /><br /> 指定主機物件執行個體 (可以為 Null)。 如果主機 IDE 讓主機物件與這個特定工作產生關聯，則建置引擎會設定這個屬性。|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|選擇性 <xref:Microsoft.Build.Utilities.TaskLoggingHelper> 唯讀參數。<br /><br /> 取得包含工作記錄方法的 `TaskLoggingHelperExtension` 物件。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
