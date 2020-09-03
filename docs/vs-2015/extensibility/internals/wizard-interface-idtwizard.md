---
title: Wizard 介面 (IDTWizard) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78867fa94851e373ae4d47cd82cd1084a941638c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180358"
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

整合式開發環境 (IDE) 會使用 <xref:EnvDTE.IDTWizard> 介面來與嚮導進行通訊。 您必須執行這個介面，才能將它安裝在 IDE 中。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>方法是唯一與介面相關聯的方法 <xref:EnvDTE.IDTWizard> 。 嚮導會執行這個方法，而 IDE 會呼叫介面上的方法。 下列範例顯示方法的簽章。  
  
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
  
 **新專案**和 [**加入新**專案] 嚮導的啟動機制很類似。 若要啟動，您可以呼叫 <xref:EnvDTE.IDTWizard> Dteinternal 中定義的介面。 唯一的差別在於呼叫介面時，會傳遞給介面的內容和自訂參數的集合。  
  
 下列資訊說明 <xref:EnvDTE.IDTWizard> 嚮導必須在 IDE 中執行才能運作的介面 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 IDE <xref:EnvDTE.IDTWizard.Execute%2A> 會在嚮導上呼叫方法，並將下列內容傳遞給它：  
  
- DTE 物件  
  
     DTE 物件是 Automation 模型的根。  
  
- [視窗] 對話方塊的控制碼，如程式碼區段中所示 `hwndOwner ([in] long)` 。  
  
     Wizard 會使用這個 `hwndOwner` 作為 wizard 對話方塊的父代。  
  
- 將內容參數當作 SAFEARRAY 的變異傳遞給介面，如程式碼區段中所示 `[in] SAFEARRAY (VARIANT)* ContextParams` 。  
  
     內容參數包含值陣列，這些值是所啟動的 wizard 類型和專案目前狀態的特定值。 IDE 會將內容參數傳遞至 wizard。 如需詳細資訊，請參閱 [內容參數](../../extensibility/internals/context-parameters.md)。  
  
- 將自訂參數當作 SAFEARRAY 的變異傳遞給介面，如程式碼區段中所示 `[in] SAFEARRAY (VARIANT)* CustomParams` 。  
  
     自訂參數包含使用者定義參數的陣列。 .Vsz 檔會將自訂參數傳遞至 IDE。 這些值是由語句所決定 `Param=` 。 如需詳細資訊，請參閱 [自訂參數](../../extensibility/internals/custom-parameters.md)。  
  
- 介面的傳回值為  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [嚮導](../../extensibility/internals/wizards.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
