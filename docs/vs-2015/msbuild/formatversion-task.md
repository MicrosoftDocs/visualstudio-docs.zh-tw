---
title: FormatVersion 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149619"
---
# <a name="formatversion-task"></a>FormatVersion 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將修訂編號附加至版本號碼。  
  
- 案例 #1：輸入： Version = \<undefined> ; 修訂 = \<don't care> ;  Output： OutputVersion = "1.0.0.0"  
  
- Case #2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"  
  
- 案例 #3：輸入： Version = "1.0.0.0" 修訂 = \<don't care> ; Output： OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>參數  
 下表說明 `FormatVersion` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`FormatType`|選擇性的 `String` 參數。<br /><br /> 指定格式類型。<br /><br /> -   "Version" = 版本。<br />-   "Path" = 將 "." 取代為 "_"；|  
|`OutputVersion`|選擇性的 `String` 輸出參數。<br /><br /> 指定包含修訂編號的輸出版本。|  
|`Revision`|選擇性的 `Int32` 參數。<br /><br /> 指定要附加至版本的修訂。|  
|`Version`|選擇性的 `String` 參數。<br /><br /> 指定要格式化的版本號碼字串。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [任務](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
