---
title: 自訂參數 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708939"
---
# <a name="custom-parameters"></a>自訂參數
自定義參數控制嚮導啟動後嚮導的操作。 相關的 *.vsz*檔案提供由整合式開發環境 (IDE) 打包的使用者定義參數陣列,並在精靈啟動時作為字串陣列傳遞給嚮導。 然後,嚮導分析字串陣列,並使用資訊來控制嚮導的實際操作。 這樣,嚮導可以根據 *.vsz*文件的內容自定義功能。

 上下文參數,另一方面,定義專案的狀態,當嚮導啟動。 有關詳細資訊,請參閱[中選中文字參數](../../extensibility/internals/context-parameters.md)。

 下面是具有自訂參數的 *.vsz*檔案的範例:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 *.vsz*檔案的作者添加參數的值。 當使用者在 **「檔案**」功能選單上選擇 **「新專案**」或 **「新增新專案**」時,或透過右鍵單擊**解決方案資源管理器**中的專案,IDE 將這些值收集到字串陣列中。 然後,IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A><xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>使用 標誌集調用專案的方法,專案調用負責運行嚮導並<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>返回結果 的方法。

 嚮導負責分析字串陣列並適當地對字串進行操作。 通過這種方式,通過實現自定義參數,您可以創建一個執行各種功能的嚮導。 換句話說,一個嚮導可以有三個不同的 *.vsz*檔。 每個文件傳遞不同的自定義參數集,以控制嚮導在各種情況下的行為。

 有關詳細資訊,請參閱精靈[(.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [內容參數](../../extensibility/internals/context-parameters.md)
- [嚮導](../../extensibility/internals/wizards.md)
- [匯入匯(.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
