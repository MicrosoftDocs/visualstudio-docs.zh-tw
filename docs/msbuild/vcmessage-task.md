---
title: "VCMessage 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.vcmessage
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
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 70f83ba6a48df66f9105d39570e0d5490f818e73
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vcmessage-task"></a>VCMessage 工作
在組建期間記錄警告和錯誤訊息。  
  
## <a name="remarks"></a>備註  
 此工作可協助實作 MSBuild for Visual C++，並不是要供使用者呼叫。 如需詳細資訊，請參閱<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。  
  
## <a name="parameters"></a>參數  
 下表描述 **VCMessage** 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|**引數**|選擇性的 **String** 參數。<br /><br /> 要顯示的訊息清單 (以分號分隔)。|  
|**程式碼**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|  
|**Type**|選擇性的 **String** 參數。<br /><br /> 指定要發出訊息的類型。 指定 `"Warning"` 發出警告訊息，或 `"Error"` 發出錯誤訊息。|  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)