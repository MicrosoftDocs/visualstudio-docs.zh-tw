---
title: Enens微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711860"
---
# <a name="enumerators"></a>列舉值
本節列出了原始程式碼管理外掛程式 API 中的枚舉器數據類型,原始程式碼管理外掛程式必須瞭解這些資料類型。

## <a name="in-this-section"></a>本節內容
- [命令代碼](../extensibility/command-code-enumerator.md)枚舉[SccGet命令選項](../extensibility/sccgetcommandoptions-function.md)和[Scc 填充清單](../extensibility/sccpopulatelist-function.md)函數的選項。

- [訊息](../extensibility/message-enumerator.md)枚舉用於列印回調[、LPTEXTOUTPROC](../extensibility/lptextoutproc.md)的標誌。

- [檔案狀態代碼](../extensibility/file-status-code-enumerator.md)包含指定來源控制下檔案狀態的命名常量值。

- [目錄狀態代碼](../extensibility/directory-status-code-enumerator.md)包含指定來源控制下的目錄狀態的命名常量值。

## <a name="related-sections"></a>相關章節
- [建立原始碼管理外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)定義原始程式碼管理外掛程式 SDK 並描述包含的資源。

- [SccGet 命令選項](../extensibility/sccgetcommandoptions-function.md)提示用戶為給定命令提供高級選項。

- [Scc填充清單](../extensibility/sccpopulatelist-function.md)檢查檔案清單的目前狀態。 此外,當檔與`pfnPopulate`的條件`nCommand`不匹配時,使用函數通知調用方。

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)描述[SccOpenProject](../extensibility/sccopenproject-function.md)用於透過 IDE 顯示來自原始碼管理外掛程式的消息的回調功能。

- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)提供原始程式碼管理外掛程式 API 中所有元素的完整清單。
