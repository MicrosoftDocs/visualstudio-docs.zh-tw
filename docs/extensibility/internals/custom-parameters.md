---
title: "自訂參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f04251ea8141d07a52499beae46b2881814eec9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="custom-parameters"></a>自訂參數
啟動精靈之後自訂參數可控制精靈 的作業。 關聯的.vsz 檔案提供整合式的開發環境 (IDE) 來封裝並啟動精靈時以字串的陣列傳遞給精靈的使用者定義參數的陣列。 然後精靈會剖析字串的陣列，並使用的資訊來控制精靈的實際操作。 如此一來，精靈可以自訂功能，根據.vsz 檔案內容而定。  
  
 啟動精靈時，內容參數，相反地，定義專案的狀態。 如需詳細資訊，請參閱[內容參數](../../extensibility/internals/context-parameters.md)。  
  
 以下是具有自訂參數.vsz 檔案的範例：  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 檔案的作者加入參數的值。 當使用者選取**新專案**或**加入新項目**檔案 功能表上，或以滑鼠右鍵按一下專案，以在**方案總管 中**，IDE 會收集下列值的陣列字串。 IDE，然後呼叫專案的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>旗標設定，而且此專案會呼叫<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>負責執行此精靈，並傳回結果的方法。  
  
 精靈會負責剖析字串的陣列，然後適當地將字串上做的。 在這種方式，藉由實作自訂參數您可以建立一個精靈，執行各式各樣函式。 換句話說，精靈可能會有三個不同.vsz 檔案。 每個檔案會傳遞不同的自訂參數來控制精靈，在各種情況下的行為集合。  
  
 如需詳細資訊，請參閱[精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)