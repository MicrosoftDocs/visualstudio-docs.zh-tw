---
title: Wizard (。.Vsz) 檔案 |Microsoft Docs
description: 深入瞭解 IDE 用來啟動嚮導的 .vsz 檔。 這些檔案包含要呼叫哪個 wizard 以及要傳遞至 wizard 的資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2663a6b05780b16d05b419c00aba904ded848796
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074232"
---
# <a name="wizard-vsz-file"></a>精靈檔 (.Vsz)

整合式開發環境 (IDE) 使用 .vsz 檔案來啟動嚮導。 這些 .vsz 檔案包含的資訊，可讓 IDE 用來判斷要呼叫的 wizard 以及要傳遞給嚮導的資訊。

.Vsz 檔案是沒有區段的 .ini 格式文字檔的版本。 IDE 已知的資訊會儲存在檔案的開頭。 這會在嚮導之間提供一個連結，IDE 會在此呼叫，以及要傳遞至 IDE 的 .vsz 檔案中的參數。 檔案的其餘部分會提供 wizard 專屬的參數，以及 IDE 所要收集並傳遞至特定 wizard 的參數。

下列範例會顯示 .vsz 檔案的內容。

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

以下是 .vsz 檔案中的部分。

|部分|描述|
|----------|-----------------|
|VSWizard|檔案中的第一個參數是範本檔案格式的版本號碼。 此版本號碼必須是6.0、7.0、7.1 或8.0。 無法啟動其他數位，而且會導致不正確格式錯誤。|
|精靈|此欄位包含 wizard 的 OLE ProgID，或 IDE 所 cocreated 的 wizard CLSID 的 GUID 字串表示。|
|Param|這些部分是選擇性的。 您可以視需要新增多個。|

參數可讓 .vsz 檔案將其他自訂參數傳遞至 wizard。 每個值都會以 variant 陣列中的字串元素形式傳遞給 wizard。 如需詳細資訊，請參閱 [自訂參數](../../extensibility/internals/custom-parameters.md)。

若要將預設的地區設定識別碼加入至 .vsz 檔案，請指定 `FALLBACK_LCID` = xxxx，其中 xxxx 是地區設定識別碼，例如，1033代表英文。 當 `FALLBACK_LCID` 參數已定義時，如果找不到目前的識別碼，則嚮導會使用提供的 fallback 地區設定識別碼。

## <a name="see-also"></a>另請參閱

- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [精靈](../../extensibility/internals/wizards.md)
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
