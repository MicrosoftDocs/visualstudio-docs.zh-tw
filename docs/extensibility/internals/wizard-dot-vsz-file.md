---
title: "精靈 (。Vsz) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7f4abe6240f799ed6db71fcf04a40774facaf6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-vsz-file"></a>精靈 (。Vsz) 檔案
整合式的開發環境 (IDE) 會使用.vsz 檔案來啟動精靈。 這些.vsz 檔案包含用來判斷要呼叫哪一個精靈的 IDE 資訊和要傳遞給精靈的資訊。  
  
 .Vsz 檔案是沒有區段.ini 格式的文字檔案的版本。 IDE 已知的資訊會儲存在檔案開頭。 這會提供 IDE 呼叫的精靈與所要傳遞給 IDE.vsz 檔案中的參數之間的連結。 檔案的其餘部分提供的參數特有精靈，而且是由 IDE 所要收集並傳遞給特定的精靈。  
  
 下列範例顯示.vsz 檔案的內容。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 以下是.vsz 檔案中的組件。  
  
|組件|說明|  
|----------|-----------------|  
|VSWizard|在檔案中的第一個參數是範本檔案格式的版本號碼。 此版本號碼必須是 6.0、 7.0、 7.1、 或 8.0。 其他數字無法啟動，並會導致不正確的格式錯誤。|  
|精靈|此欄位會包含 OLE ProgID 的精靈，或者 cocreated ide 在精靈的 CLSID 的 GUID 字串表示。|  
|參數|這些組件是選擇性的。 您可以新增多達所需。|  
  
 參數可讓將其他自訂參數傳遞給精靈.vsz 檔案。 每個值當做字串中的項目 variant 的陣列傳遞至精靈。 如需詳細資訊，請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。 如需如何使用開發工作的自訂精靈.vsz 檔案資訊，請參閱[。Vsz 檔案 （專案控制）](/cpp/ide/dot-vsz-file-project-control)  
  
 若要加入.vsz 檔案中的預設地區設定識別碼，請指定`FALLBACK_LCID`= 的 xxxx，其中 xxxx 會是地區設定識別碼，例如，1033 代表英文。 當`FALLBACK_LCID`參數定義、 找不到目前的識別碼時，精靈會使用提供的後援地區設定識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)