---
title: 嚮導介面 (IDTWizard) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703269"
---
# <a name="wizard-interface-idtwizard"></a>精靈介面 (IDTWizard)
集成開發環境 (IDE)<xref:EnvDTE.IDTWizard>使用 該介面與嚮導進行通信。 嚮導必須實現此介面才能安裝在 IDE 中。

 該方法<xref:EnvDTE.IDTWizard.Execute%2A>是與介面關聯的唯<xref:EnvDTE.IDTWizard>一 方法。 嚮導實現此方法,IDE 調用介面上的方法。 下面的示例顯示了方法的簽名。

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

 新**專案**「和 **」添加新專案**「嚮導的啟動機制類似。 要啟動這兩個,您<xref:EnvDTE.IDTWizard>調用在 Dtein.h 中定義的介面。 唯一的區別是調用介面時傳遞給介面的上下文和自定義參數集。

 以下資訊描述了嚮導在<xref:EnvDTE.IDTWizard>[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 中工作時必須實現的介面。 IDE 調用嚮<xref:EnvDTE.IDTWizard.Execute%2A>導 上的方法,傳遞如下:

- DTE 物件

     DTE 對像是自動化模型的根。

- 視窗對話框的句柄,如代碼欄位所`hwndOwner ([in] long)`示 。

     嚮導使用此選項`hwndOwner`項作為嚮導對話框的父級。

- 上下文參數作為 SAFEARRAY 的變體傳遞給`[in] SAFEARRAY (VARIANT)* ContextParams`介面, 如代碼段所示。

     上下文參數包含特定於正在啟動的嚮導類型和專案的當前狀態的值陣列。 IDE 將上下文參數傳遞給嚮導。 有關詳細資訊,請參閱[中選中文字參數](../../extensibility/internals/context-parameters.md)。

- 自定義參數作為 SAFEARRAY 的變體傳遞給`[in] SAFEARRAY (VARIANT)* CustomParams`介面, 如代碼段所示。

     自定義參數包含使用者定義的參數陣列。 .vsz 檔案將自定義參數傳遞給 IDE。 這些值由`Param=`語句確定。 有關詳細資訊,請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。

- 介面傳回值為

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>另請參閱
- [內容參數](../../extensibility/internals/context-parameters.md)
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [嚮導](../../extensibility/internals/wizards.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
