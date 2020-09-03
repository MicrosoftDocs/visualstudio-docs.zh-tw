---
title: 自訂參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154995"
---
# <a name="custom-parameters"></a>自訂參數
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

自訂參數會在啟動嚮導之後控制 wizard 的操作。 相關的 .vsz 檔案會提供由整合式開發環境 (IDE) 的使用者定義參數陣列，並在啟動嚮導時，將其當作字串陣列傳遞給 wizard。 接著，嚮導會剖析字串陣列，並使用此資訊來控制 wizard 的實際操作。 透過這種方式，嚮導可以根據 .vsz 檔案的內容來自訂功能。  
  
 相反地，內容參數會在啟動嚮導時定義專案的狀態。 如需詳細資訊，請參閱 [內容參數](../../extensibility/internals/context-parameters.md)。  
  
 以下是具有自訂參數的 .vsz 檔案範例：  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 檔案的作者會加入參數的值。 當使用者在 [檔案] 功能表上選取 [ **新增專案** ] 或 [ **加入新** 專案]，或是以滑鼠右鍵按一下 [ **方案總管**] 中的專案時，IDE 會將這些值收集到字串陣列中。 然後，IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 會使用設定的旗標來呼叫專案的方法 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> ，而專案 <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> 會呼叫負責執行嚮導並傳回結果的方法。  
  
 Wizard 負責剖析字串陣列，並適當地處理字串。 透過這種方式，您可以藉由執行自訂參數，建立一個執行各種功能的 wizard。 換句話說，一個 wizard 可以有三個不同的 .vsz 檔。 每個檔案都會傳遞不同的自訂參數集，以在各種情況下控制 wizard 的行為。  
  
 如需詳細資訊，請參閱 [Wizard (。.Vsz) ](../../extensibility/internals/wizard-dot-vsz-file.md)檔。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [嚮導](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
