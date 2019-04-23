---
title: VCMessage 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 508d1fe33046f6051c9c5c1b8e54036e78ae7d2f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652367"
---
# <a name="vcmessage-task"></a>VCMessage 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在組建期間記錄警告和錯誤訊息。  
  
## <a name="remarks"></a>備註  
 此工作可協助實作 MSBuild for Visual C++，並不是要供使用者呼叫。 如需詳細資訊，請參閱<xref:Microsoft.Build.Utilities.TaskLoggingHelper>。  
  
## <a name="parameters"></a>參數  
 下表描述 **VCMessage** 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|**引數**|選擇性的 **String** 參數。<br /><br /> 要顯示的訊息清單 (以分號分隔)。|  
|**程式碼**|必要的 **String** 參數。<br /><br /> 限定訊息的錯誤號碼。|  
|**Type**|選擇性的 **String** 參數。<br /><br /> 指定要發出訊息的類型。 指定 `"Warning"` 發出警告訊息，或 `"Error"` 發出錯誤訊息。|  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)
