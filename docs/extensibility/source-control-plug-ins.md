---
title: 源代碼管理外掛程式 |微軟文件
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
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699896"
---
# <a name="source-control-plug-ins"></a>原始檔控制外掛程式
原始程式碼管理外掛程式 SDK 參考部分包含完整的介面規範,使原始程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]碼管理系統能夠與整合。 它指定原始程式碼管理外掛程式必須實現的各種函數和資料類型的語法和語義,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以便與整合式開發環境 (IDE) 介面。

## <a name="in-this-section"></a>本節內容
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)列出原始碼管理外掛程式必須實現的函數,以便符合原始程式碼管理外掛程式 API。

- [IDE 實現的回檔函式](../extensibility/callback-functions-implemented-by-the-ide.md)描述原始程式管理外掛程式在執行某些命令時用於將資訊傳回 IDE 的功能。

- [Ent](../extensibility/enumerators.md)在原始程式碼管理外掛程式 API 中列出來源控制元件 API 中的枚舉器數據類型,原始程式碼管理外掛程式必須瞭解這些資料類型。

- [功能旗標](../extensibility/capability-flags.md)描述`SCC_CAP_xxx`標誌,這些標誌表示提供程式的功能。

- [特定指令使用的位元號](../extensibility/bitflags-used-by-specific-commands.md)列出在特定命令的上下文中有用的標誌。

- [錯誤代碼](../extensibility/error-codes.md)將函數傳回的錯誤值列為`SCCTRN`。

- [以找原始碼管理外掛程式鍵](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)描述訪問註冊表以查找原始程式碼管理外掛程式的鍵。

- [MSSCCPRJ.SCC 檔](../extensibility/mssccprj-scc-file.md)描述包含對 IDE 不透明的資訊,但原始程式碼管理外掛程式用於在版本控制中尋找解決方案或專案的用戶端檔。

- [實現原始碼管理外掛程式的最佳做法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)提供在實現原始程式碼管理外掛程式 API 時要記住的重要技術提醒的集合。

- [字串長度的限制](../extensibility/restrictions-on-string-lengths.md)描述原始碼管理外掛程式 API 中對各種函數中使用的字串長度的限制。

- [詞彙表](../extensibility/source-control-plug-in-glossary.md)提供了用於閱讀原始程式碼管理外掛程式 SDK 文件的有用術語及其定義。

- [如何:關閉原始碼管理外掛程式的相容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)描述如何禁用警告。

## <a name="related-sections"></a>相關章節
- [原始程式管理外掛程式範例](https://www.microsoft.com/download/details.aspx?id=55984)提供原始程式碼管理外掛程式功能的範例。

- [源代碼管理外掛程式測試指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)描述與原始程式碼管理外掛程式相關的測試過程。

- [建立原始碼管理外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)討論如何在使用原始程式碼管理使用者介面 (UI) 時建立提供原始碼[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]管理功能的原始程式管理外掛程式。

- [視覺化工作室 SDK 參考](../extensibility/visual-studio-sdk-reference.md)顯示參考主題的清單。
