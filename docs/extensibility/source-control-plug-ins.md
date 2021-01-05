---
title: 原始檔控制外掛程式 |Microsoft Docs
description: 本節中的文章描述可讓原始檔控制系統與 Visual Studio 整合的完整介面規格。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617b06e46bb150026f49af3e23761dfd6cb4e902
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715830"
---
# <a name="source-control-plug-ins"></a>原始檔控制外掛程式
原始檔控制外掛程式 SDK 參考區段包含可讓原始檔控制系統與整合的完整介面規格 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 它會指定原始檔控制外掛程式必須執行的各種函式和資料類型的語法和語義，以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE) 的整合式開發環境進行介面。

## <a name="in-this-section"></a>本節內容
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md) 列出必須由原始檔控制外掛程式執行的函式，才能符合原始檔控制外掛程式 API。

- [IDE 所執行的回呼函數](../extensibility/callback-functions-implemented-by-the-ide.md) 描述當執行某些命令時，原始檔控制外掛程式用來將資訊傳遞回 IDE 的函式。

- [枚舉](../extensibility/enumerators.md) 器列出原始檔控制外掛程式必須知道的原始檔控制外掛程式 API 中的列舉值資料類型。

- [功能旗標](../extensibility/capability-flags.md) 描述 `SCC_CAP_xxx` 旗標，這些旗標表示提供者的功能。

- [特定命令所使用的位旗標](../extensibility/bitflags-used-by-specific-commands.md) 列出適用于特定命令內容的旗標。

- [錯誤碼](../extensibility/error-codes.md) 列出函數所傳回的常見錯誤值 `SCCTRN` 。

- [用來作為用來尋找原始檔控制外掛程式之索引鍵的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) 描述用來存取登錄以尋找原始檔控制外掛程式的索引鍵。

- [Mssccprj.scc。SCC](../extensibility/mssccprj-scc-file.md) 檔案會描述用戶端檔案，其中包含 IDE 的不透明資訊，但原始檔控制外掛程式會使用此檔案來尋找版本控制中的方案或專案。

- [執行原始檔控制外掛程式的最佳作法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) 提供當您在執行原始檔控制外掛程式 API 時要記住的重要技術提醒集合。

- [字串長度的限制](../extensibility/restrictions-on-string-lengths.md) 描述原始檔控制外掛程式 API 中用於各種函式的字串長度限制。

- [詞彙](../extensibility/source-control-plug-in-glossary.md) 提供實用的詞彙及其定義，以讀取原始檔控制外掛程式 SDK 檔。

- [如何：關閉原始檔控制外掛程式的相容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) 說明如何停用警告。

## <a name="related-sections"></a>相關章節
- [原始檔控制外掛程式範例](https://www.microsoft.com/download/details.aspx?id=55984) 提供原始檔控制外掛程式功能的範例。

- [原始檔控制外掛程式的測試指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md) 描述與原始檔控制外掛程式相關的測試程式。

- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md) 討論如何建立原始檔控制外掛程式，以在您使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 原始檔控制使用者介面 (UI) 時提供原始檔控制功能。

- [VISUAL STUDIO SDK 參考](../extensibility/visual-studio-sdk-reference.md) 提供參考主題的清單。
