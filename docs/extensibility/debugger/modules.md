---
title: 模組 |Microsoft Docs
description: 本文說明 Visual Studio 中偵錯工具架構中模組的定義和角色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926326"
---
# <a name="modules"></a>單元
就偵錯工具架構而言， *模組*：

- 是程式碼的實體容器，例如可執行檔或 DLL。

- 可以重載其符號並加以描述。 模組描述會顯示在 IDE 的 [模組] 視窗中。

- 是由偵錯工具引擎所建立的 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 介面所表示，用來描述模組。

## <a name="see-also"></a>另請參閱
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
