---
title: 列舉值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334501"
---
# <a name="enumerators"></a>列舉程式
此區段會列出原始檔控制外掛程式必須了解原始檔控制外掛程式 API 中的列舉值資料類型。

## <a name="in-this-section"></a>本節內容
- [命令的程式碼](../extensibility/command-code-enumerator.md)列舉的選項[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)並[SccPopulateList](../extensibility/sccpopulatelist-function.md)函式。

- [訊息](../extensibility/message-enumerator.md)旗標用於列印的回呼，會列舉[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。

- [檔案狀態碼](../extensibility/file-status-code-enumerator.md)包含名為指定的原始檔控制下的檔案狀態的常數值。

- [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)包含名為指定的原始檔控制之下的目錄狀態的常數值。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)定義原始檔控制外掛程式 SDK，並說明內含的資源。

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)提示使用者提供指定的命令的進階選項。

- [SccPopulateList](../extensibility/sccpopulatelist-function.md)會檢查其目前狀態的檔案清單。 此外，會使用`pfnPopulate`檔案類型不符合的準則時告知呼叫端函式`nCommand`。

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)描述的回呼函式，以供[SccOpenProject](../extensibility/sccopenproject-function.md)顯示從原始檔控制外掛程式，透過 IDE 的訊息。

- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)提供完整的原始檔控制外掛程式 API 中的所有項目清單。