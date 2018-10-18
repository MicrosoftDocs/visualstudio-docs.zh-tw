---
title: 自訂參數 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8831517b7b679762e12356927b39e244a2a5dd1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305394"
---
# <a name="custom-parameters"></a>自訂參數
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

啟動精靈之後自訂參數可控制精靈的作業。 相關的.vsz 檔案提供整合式的開發環境 (IDE) 封裝並啟動精靈時，傳遞給精靈的字串陣列作為使用者定義的參數陣列。 精靈接著會剖析的字串陣列，並使用的資訊，來控制精靈 的實際作業。 如此一來，精靈可以自訂功能取決於.vsz 檔案的內容。  
  
 啟動精靈時，內容參數，相反地，定義專案的狀態。 如需詳細資訊，請參閱 <<c0> [ 內容參數](../../extensibility/internals/context-parameters.md)。  
  
 以下是具有自訂參數的.vsz 檔案的範例：  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 檔案的作者加入參數的值。 當使用者選取**新的專案**或是**加入新項目**檔案 功能表上，或以滑鼠右鍵按一下專案，以在**方案總管 中**，IDE 會收集下列值的陣列字串。 IDE 接著會呼叫專案組<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>旗標集，以及專案呼叫<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>負責執行精靈，並傳回結果的方法。  
  
 精靈會負責剖析的字串陣列，並適當地做對的字串。 以這種方式，藉由實作自訂參數您可以建立一個會執行各種函式的精靈。 換句話說，只需要一個精靈可能會有三個不同的.vsz 檔案。 每個檔案會傳遞不同的自訂參數來控制精靈，在各種情況下的行為。  
  
 如需詳細資訊，請參閱[精靈 (。在 Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

