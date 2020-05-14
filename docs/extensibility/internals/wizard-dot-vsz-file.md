---
title: 嚮導 (.Vsz) 檔案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703316"
---
# <a name="wizard-vsz-file"></a>精靈檔 (.Vsz)

整合式開發環境 (IDE) 使用 .vsz 檔案啟動精靈。 這些 .vsz 檔包含 IDE 用於確定呼叫哪個精靈以及要傳遞給精靈的資訊的資訊。

.vsz 檔案是 .ini 格式的文本檔的版本,該檔沒有節。 IDE 已知的資訊存儲在檔的開頭。 這提供了 IDE 調用的嚮導和要傳遞給 IDE 的 .vsz 檔案中的參數之間的連結。 檔的其餘部分提供特定於嚮導的參數,這些參數將由IDE收集並傳遞給特定嚮導。

下面的範例顯示 .vsz 文件的內容。

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

以下是 .vsz 檔案中的部分。

|部分|描述|
|----------|-----------------|
|VSWizard|檔案中的第一個參數是範本檔案格式的版本號。 此版本號必須為 6.0、7.0、7.1 或 8.0。 無法啟動其他數位並導致格式無效錯誤。|
|精靈|此欄位包含精靈的 OLE ProgID,或者包含由 IDE 共同建立的嚮導 CLSID 的 GUID 字串表示形式。|
|Param|這些部件是可選的。 您可以根據需要添加盡可能多的。|

這些參數使 .vsz 檔案能夠將其他自定義參數傳遞給嚮導。 每個值都作為字串元素傳遞給嚮導的變數組中。 有關詳細資訊,請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。

要將預設區域設定 ID 添加到 .vsz 檔案`FALLBACK_LCID`,請指定 _xxxx,其中 xxx 是區域設定 ID,例如,英語為 1033。 定義`FALLBACK_LCID`參數時,如果未找到當前 ID,嚮導將使用提供的回退區域設置 ID。

## <a name="see-also"></a>另請參閱

- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [嚮導](../../extensibility/internals/wizards.md)
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
