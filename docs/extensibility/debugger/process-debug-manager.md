---
title: 進程 Debug Manager |Microsoft Docs
description: 瞭解「進程偵錯工具」，這是 Visual Studio 的元件，可讓「會話偵錯工具管理員」和「debug 引擎」使用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- machine debug manager
- debugging [Debugging SDK], Machine Debug Manager
ms.assetid: d0861e0c-b819-490c-9604-5e6d08ac291a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c332b28e48b24065b5e359332df65c61365f1763
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067720"
---
# <a name="process-debug-manager"></a>進程偵錯工具管理員
進程 debug manager (PDM) 是管理程式和進程的 Visual Studio 元件，可供會話 debug manager 和 debug engine 使用。

 PDM 會管理所有可進行調試的進程。 若要進行調試，必須向 PDM 註冊程式。 此註冊會在程式啟動時完成，無論是由埠或 debug 引擎進行。

## <a name="see-also"></a>另請參閱
- [處理序](../../extensibility/debugger/processes.md)
- [Debug 引擎](../../extensibility/debugger/debug-engine.md)
- [連接埠](../../extensibility/debugger/ports.md)
- [程式](../../extensibility/debugger/programs.md)
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
