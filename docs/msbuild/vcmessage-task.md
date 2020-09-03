---
title: VCMessage 工作 | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631207"
---
# <a name="vcmessage-task"></a>VCMessage 工作

在組建期間記錄警告和錯誤訊息。

## <a name="remarks"></a>備註

 這項工作可協助針對 c + + 專案執行 MSBuild，而不是供使用者呼叫。 如需詳細資訊，請參閱<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。

## <a name="parameters"></a>參數

 下表描述 **VCMessage** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**引數**|選擇性的 **字串** 參數。<br /><br /> 要顯示的訊息清單 (以分號分隔)。|
|**程式碼**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|
|**類型**|選擇性的 **字串** 參數。<br /><br /> 指定要發出訊息的類型。 指定「警告」發出警告訊息，或「錯誤」發出錯誤訊息。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
