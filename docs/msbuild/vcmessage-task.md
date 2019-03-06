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
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d025fd1f71b67acbcd532232b36b55fd35e1f530
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596057"
---
# <a name="vcmessage-task"></a>VCMessage 工作
在組建期間記錄警告和錯誤訊息。

## <a name="remarks"></a>備註
 此工作可協助實作 MSBuild for Visual C++，並不是要供使用者呼叫。 如需詳細資訊，請參閱<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。

## <a name="parameters"></a>參數
 下表描述 **VCMessage** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**引數**|選擇性的 **String** 參數。<br /><br /> 要顯示的訊息清單 (以分號分隔)。|
|**程式碼**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|
|**Type**|選擇性的 **String** 參數。<br /><br /> 指定要發出訊息的類型。 指定「警告」發出警告訊息，或「錯誤」發出錯誤訊息。|

## <a name="see-also"></a>另請參閱
- [工作參考](../msbuild/msbuild-task-reference.md)