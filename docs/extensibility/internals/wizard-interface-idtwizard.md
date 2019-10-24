---
title: Wizard 介面（IDTWizard） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721536"
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
整合式開發環境（IDE）會使用 <xref:EnvDTE.IDTWizard> 介面來與嚮導進行通訊。 必須執行此介面，才能在 IDE 中安裝。

 @No__t_0 方法是與 <xref:EnvDTE.IDTWizard> 介面相關聯的唯一方法。 嚮導會執行這個方法，而 IDE 會在介面上呼叫方法。 下列範例會顯示方法的簽章。

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

 [**新增專案**] 和 [**加入新**專案] 嚮導的 [啟動] 機制很類似。 若要啟動，請呼叫 Dteinternal 中定義的 <xref:EnvDTE.IDTWizard> 介面。 唯一的差異在於呼叫介面時，傳遞至介面的內容和自訂參數集合。

 下列資訊說明在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，必須執行的 <xref:EnvDTE.IDTWizard> 介面。 IDE 會在 wizard 上呼叫 <xref:EnvDTE.IDTWizard.Execute%2A> 方法，並將下列內容傳遞給它：

- DTE 物件

     DTE 物件是 Automation 模型的根。

- [視窗] 對話方塊的控制碼（如程式碼區段中所示） `hwndOwner ([in] long)`。

     Wizard 使用此 `hwndOwner` 作為 [wizard] 對話方塊的父系。

- 以 SAFEARRAY 的 variant 形式傳遞給介面的內容參數（如程式碼區段中所示），`[in] SAFEARRAY (VARIANT)* ContextParams`。

     內容參數包含值的陣列，這些值是所啟動的 wizard 和專案的目前狀態所特有。 IDE 會將內容參數傳遞至 wizard。 如需詳細資訊，請參閱[內容參數](../../extensibility/internals/context-parameters.md)。

- 以 SAFEARRAY 的 variant 形式傳遞至介面的自訂參數（如程式碼區段中所示），`[in] SAFEARRAY (VARIANT)* CustomParams`。

     自訂參數包含使用者定義參數的陣列。 .Vsz 檔案會將自訂參數傳遞至 IDE。 這些值取決於 `Param=` 語句。 如需詳細資訊，請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。

- 介面的傳回值為

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>請參閱
- [內容參數](../../extensibility/internals/context-parameters.md)
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [精靈](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)