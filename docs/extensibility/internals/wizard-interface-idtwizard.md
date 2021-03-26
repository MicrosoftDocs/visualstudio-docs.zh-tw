---
title: Wizard 介面 (IDTWizard) |Microsoft Docs
description: IDE 會使用 IDTWizard 介面來與嚮導進行通訊。 您必須將此介面實作為安裝在 IDE 中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8dc88341bc72755ae0f5011d18182c5b78bb483
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074193"
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
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

 **新專案** 和 [**加入新** 專案] 嚮導的啟動機制很類似。 若要啟動，您可以呼叫 <xref:EnvDTE.IDTWizard> Dteinternal 中定義的介面。 唯一的差別在於呼叫介面時，會傳遞給介面的內容和自訂參數的集合。

 下列資訊說明 <xref:EnvDTE.IDTWizard> 嚮導必須在 IDE 中執行才能運作的介面 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 IDE <xref:EnvDTE.IDTWizard.Execute%2A> 會在嚮導上呼叫方法，並將下列內容傳遞給它：

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
- [內容參數](../../extensibility/internals/context-parameters.md)
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [精靈](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
