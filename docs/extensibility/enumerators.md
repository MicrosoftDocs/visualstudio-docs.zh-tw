---
title: 枚舉器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711860"
---
# <a name="enumerators"></a>列舉值
此區段會列出原始檔控制外掛程式必須知道的原始檔控制外掛程式 API 中的列舉值資料類型。

## <a name="in-this-section"></a>本節內容
- [命令碼](../extensibility/command-code-enumerator.md) 列舉 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 函數的選項。

- [訊息](../extensibility/message-enumerator.md) 列舉用於列印回呼、 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)的旗標。

- 檔案[狀態碼](../extensibility/file-status-code-enumerator.md)包含指定原始檔控制下之檔案狀態的指定常數值。

- [目錄狀態碼](../extensibility/directory-status-code-enumerator.md) 包含指定原始檔控制下之目錄狀態的指定常數值。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md) 定義原始檔控制外掛程式 SDK 並說明包含的資源。

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 提示使用者提供指定命令的 advanced 選項。

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 檢查檔案清單中的目前狀態。 此外，當檔案不 `pfnPopulate` 符合的準則時，也會使用函式來通知呼叫端 `nCommand` 。

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 描述 [SccOpenProject](../extensibility/sccopenproject-function.md) 使用的回呼函式，以透過 IDE 顯示來自原始檔控制外掛程式的訊息。

- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md) 提供原始檔控制外掛程式 API 中所有元素的完整清單。
