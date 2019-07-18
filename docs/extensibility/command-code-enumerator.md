---
title: 命令碼列舉程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4ec14c15bbd0aa6340e30e3156e714ba5f9e074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334953"
---
# <a name="command-code-enumerator"></a>命令碼列舉程式
這個列舉值使用中的選項[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)並[SccPopulateList](../extensibility/sccpopulatelist-function.md)表示指定之選項的命令。

## <a name="syntax"></a>語法

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>成員
SCC_COMMAND_GET 等同[SccGet](../extensibility/sccget-function.md)。

SCC_COMMAND_CHECKOUT 等同[SccCheckout](../extensibility/scccheckout-function.md)。

SCC_COMMAND_CHECKIN 等同[SccCheckin](../extensibility/scccheckin-function.md)。

SCC_COMMAND_UNCHECKOUT 等同[SccUncheckout](../extensibility/sccuncheckout-function.md)。

SCC_COMMAND_ADD 等同[SccAdd](../extensibility/sccadd-function.md)。

SCC_COMMAND_REMOVE 等同[SccRemove](../extensibility/sccremove-function.md)。

SCC_COMMAND_DIFF 等同[SccDiff](../extensibility/sccdiff-function.md)。

SCC_COMMAND_HISTORY 等同[SccHistory](../extensibility/scchistory-function.md)。

SCC_COMMAND_RENAME 等同[SccRename](../extensibility/sccrename-function.md)。

SCC_COMMAND_PROPERTIES 等同[SccProperties](../extensibility/sccproperties-function.md)。

SCC_COMMAND_OPTIONS 等同[SccSetOption](../extensibility/sccsetoption-function.md)。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
