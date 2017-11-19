---
title: "精靈介面 (IDTWizard) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba6952bce6d99149f2a8f18b7d2eac12cbd08761
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
整合式的開發環境 (IDE) 會使用<xref:EnvDTE.IDTWizard>與精靈通訊的介面。 精靈必須實作這個介面，才能安裝在 IDE 中。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>方法是相關聯的唯一方法<xref:EnvDTE.IDTWizard>介面。 精靈會實作這個方法，並在 IDE 介面上呼叫方法。 下列範例會顯示方法的簽章。  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 啟動機制都很相似**新專案**和**加入新項目**精靈。 若要啟動 ，呼叫<xref:EnvDTE.IDTWizard>Dteinternal.h 中定義的介面。 唯一的差別是一組內容和時的介面稱為傳遞至介面的自訂參數。  
  
 下列資訊描述<xref:EnvDTE.IDTWizard>精靈必須實作以在介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。 IDE 呼叫<xref:EnvDTE.IDTWizard.Execute%2A>在精靈中，將其傳遞下列方法：  
  
-   DTE 物件  
  
     DTE 物件是 Automation 模型的根。  
  
-   [視窗] 對話方塊中的程式碼片段中所示的控制代碼`hwndOwner ([in] long)`。  
  
     精靈會使用此`hwndOwner`做為精靈 對話方塊的父系。  
  
-   內容參數傳遞給介面為 variant 的 SAFEARRAY 所示，在程式碼區段， `[in] SAFEARRAY (VARIANT)* ContextParams`。  
  
     內容參數包含所特有的正在啟動的精靈類型值的陣列和專案的目前狀態。 IDE 會將內容參數傳遞至精靈。 如需詳細資訊，請參閱[內容參數](../../extensibility/internals/context-parameters.md)。  
  
-   自訂參數傳遞給介面為 variant 的 SAFEARRAY 所示，在程式碼區段， `[in] SAFEARRAY (VARIANT)* CustomParams`。  
  
     自訂參數包含使用者定義的參數陣列。 .Vsz 檔案會將自訂參數傳遞至 IDE。 的值取決於`Param=`陳述式。 如需詳細資訊，請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。  
  
-   傳回值的介面  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)