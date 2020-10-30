---
title: VCMessage 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何在 c + + 專案的組建期間，使用 VCMessage 工作記錄警告和錯誤訊息。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046751"
---
# <a name="vcmessage-task"></a>VCMessage 工作

在組建期間記錄警告和錯誤訊息。

## <a name="remarks"></a>備註

 這項工作可協助針對 c + + 專案執行 MSBuild，而不是供使用者呼叫。 如需詳細資訊，請參閱<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。

## <a name="parameters"></a>參數

 下表描述 **VCMessage** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**引數**|選擇性的 **字串** 參數。<br /><br /> 要顯示的訊息清單 (以分號分隔)。|
|**程式碼**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|
|**型別**|選擇性的 **字串** 參數。<br /><br /> 指定要發出訊息的類型。 指定「警告」發出警告訊息，或「錯誤」發出錯誤訊息。|

## <a name="see-also"></a>請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
