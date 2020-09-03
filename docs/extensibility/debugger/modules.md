---
title: 模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738342"
---
# <a name="modules"></a>單元
就偵錯工具架構而言， *模組*：

- 是程式碼的實體容器，例如可執行檔或 DLL。

- 可以重載其符號並加以描述。 模組描述會顯示在 IDE 的 [模組] 視窗中。

- 是由偵錯工具引擎所建立的 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 介面所表示，用來描述模組。

## <a name="see-also"></a>另請參閱
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
