---
title: 原始檔控制外掛程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a717fdb885669ae4893dc4234c58233dec2957be
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691653"
---
# <a name="source-control-plug-ins"></a>原始檔控制外掛程式
原始檔控制外掛程式 SDK 參考章節包含可讓與整合的原始檔控制系統的完整介面規格[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 語法和語意的原始檔控制外掛程式必須實作介面以各種函式和資料類型，它會指定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。

## <a name="in-this-section"></a>本節內容
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)列出原始檔控制外掛程式必須實作才能符合原始檔控制外掛程式 API 的函式。

- [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)描述函式的原始檔控制外掛程式用來將資訊傳回給 IDE 上，執行特定命令時。

- [列舉值](../extensibility/enumerators.md)列出原始檔控制外掛程式必須了解原始檔控制外掛程式 API 中的列舉值資料類型。

- [功能旗標](../extensibility/capability-flags.md)描述`SCC_CAP_xxx`旗標，這是表示提供者的功能。

- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)列出適合特定命令的內容中的旗標。

- [錯誤碼](../extensibility/error-codes.md)列出為函式所傳回的常見錯誤值`SCCTRN`。

- [用於將字串當做索引鍵以尋找原始檔控制外掛程式](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)描述索引鍵來存取此登錄來尋找原始檔控制外掛程式。

- [MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)描述用戶端檔案，其中包含資訊的不透明的 ide，但正由原始檔控制外掛程式在版本控制中找出方案或專案。

- [實作原始檔控制外掛程式的最佳作法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)提供重要技術的提醒，請記住，當您要實作原始檔控制外掛程式 API 的集合。

- [字串長度限制](../extensibility/restrictions-on-string-lengths.md)描述用於各種不同的函式的字串長度限制在原始檔控制外掛程式 API。

- [詞彙](../extensibility/source-control-plug-in-glossary.md)提供很有幫助的詞彙和定義其讀取的原始檔控制外掛程式 SDK 文件。

- [如何：開啟關閉的相容性警告原始檔控制外掛程式](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)描述如何停用警告。

## <a name="related-sections"></a>相關章節
- [原始檔控制外掛程式範例](https://www.microsoft.com/download/details.aspx?id=55984)提供原始檔控制外掛程式功能的範例。

- [測試原始檔控制外掛程式的指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)描述原始檔控制外掛程式的相關的測試程序。

- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)討論如何建立原始檔控制外掛程式，提供原始檔控制功能，當您使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]原始檔控制使用者介面 (UI)。

- [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)顯示的參考主題清單。