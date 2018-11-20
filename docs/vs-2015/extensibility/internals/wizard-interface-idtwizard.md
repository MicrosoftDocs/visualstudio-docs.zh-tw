---
title: 精靈介面 (IDTWizard) |Microsoft Docs
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
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62ae4ab1137be452a1c769d16c153e4499a4a331
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792524"
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

整合式的開發環境 (IDE) 使用<xref:EnvDTE.IDTWizard>與精靈通訊的介面。 精靈必須實作這個介面，才能安裝在 IDE 中。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>方法是相關聯的唯一方法<xref:EnvDTE.IDTWizard>介面。 精靈會實作這個方法，IDE 會在介面上呼叫方法。 下列範例會顯示方法的簽章。  
  
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
  
 啟動機制都很相似**新的專案**並**加入新項目**精靈。 若要啟動任一個，請呼叫<xref:EnvDTE.IDTWizard>Dteinternal.h 中定義的介面。 唯一的差別是一組內容和介面呼叫時，會傳遞至介面的自訂參數。  
  
 下列資訊描述<xref:EnvDTE.IDTWizard>精靈必須用於實作的介面[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE。 IDE 呼叫<xref:EnvDTE.IDTWizard.Execute%2A>精靈中，將它傳遞下列方法：  
  
-   DTE 物件  
  
     DTE 物件是自動化模型的根。  
  
-   [視窗] 對話方塊中程式碼片段所示的控制代碼`hwndOwner ([in] long)`。  
  
     精靈會使用此`hwndOwner`為精靈 對話方塊的父代。  
  
-   內容參數傳遞給介面做為變化 SAFEARRAY 的程式碼片段所示`[in] SAFEARRAY (VARIANT)* ContextParams`。  
  
     內容參數會包含值所特有的正在啟動的精靈類型的陣列和專案的目前狀態。 IDE 會將內容參數傳遞至精靈。 如需詳細資訊，請參閱 <<c0> [ 內容參數](../../extensibility/internals/context-parameters.md)。  
  
-   自訂參數傳遞給介面做為變化 SAFEARRAY 的程式碼片段所示`[in] SAFEARRAY (VARIANT)* CustomParams`。  
  
     自訂參數會包含使用者定義的參數陣列。 .Vsz 檔案會將自訂參數傳遞至 IDE。 的值取決於`Param=`陳述式。 如需詳細資訊，請參閱 <<c0> [ 自訂參數](../../extensibility/internals/custom-parameters.md)。  
  
-   介面的傳回值  
  
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

