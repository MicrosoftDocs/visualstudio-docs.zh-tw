---
title: Wizard (。.Vsz) 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687670"
---
# <a name="wizard-vsz-file"></a>精靈檔 (.Vsz)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

整合式開發環境 (IDE) 使用 .vsz 檔案來啟動嚮導。 這些 .vsz 檔案包含的資訊，可讓 IDE 用來判斷要呼叫的 wizard 以及要傳遞給嚮導的資訊。  
  
 .Vsz 檔案是沒有區段的 .ini 格式文字檔的版本。 IDE 已知的資訊會儲存在檔案的開頭。 這會在嚮導之間提供一個連結，IDE 會在此呼叫，以及要傳遞至 IDE 的 .vsz 檔案中的參數。 檔案的其餘部分會提供 wizard 專屬的參數，以及 IDE 所要收集並傳遞至特定 wizard 的參數。  
  
 下列範例會顯示 .vsz 檔案的內容。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 以下是 .vsz 檔案中的部分。  
  
|部分|描述|  
|----------|-----------------|  
|VSWizard|檔案中的第一個參數是範本檔案格式的版本號碼。 此版本號碼必須是6.0、7.0、7.1 或8.0。 無法啟動其他數位，而且會導致不正確格式錯誤。|  
|精靈|此欄位包含 wizard 的 OLE ProgID，或 IDE 所 cocreated 的 wizard CLSID 的 GUID 字串表示。|  
|Param|這些部分是選擇性的。 您可以視需要新增多個。|  
  
 參數可讓 .vsz 檔案將其他自訂參數傳遞至 wizard。 每個值都會以 variant 陣列中的字串元素形式傳遞給 wizard。 如需詳細資訊，請參閱 [自訂參數](../../extensibility/internals/custom-parameters.md)。 如需如何在開發自訂嚮導時使用 .vsz 檔案的詳細資訊，請參閱[。 (專案控制項) 的 .vsz](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)檔案  
  
 若要將預設的地區設定識別碼加入至 .vsz 檔案，請指定 `FALLBACK_LCID` = xxxx，其中 xxxx 是地區設定識別碼，例如，1033代表英文。 當 `FALLBACK_LCID` 參數已定義時，如果找不到目前的識別碼，則嚮導會使用提供的 fallback 地區設定識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [嚮導](../../extensibility/internals/wizards.md)   
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
