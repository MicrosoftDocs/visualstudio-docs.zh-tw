---
title: 命令代碼枚舉器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739794"
---
# <a name="command-code-enumerator"></a>命令片段
此枚舉器用於[SccGetCommandOptions 和](../extensibility/sccgetcommandoptions-function.md) [Scc 填充清單](../extensibility/sccpopulatelist-function.md)的選項中,以指示為其指定選項的命令。

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
SCC_COMMAND_GET對應於[SccGet。](../extensibility/sccget-function.md)

SCC_COMMAND_CHECKOUT對應於[SccCheckout。](../extensibility/scccheckout-function.md)

SCC_COMMAND_CHECKIN對應於[SccCheckin。](../extensibility/scccheckin-function.md)

SCC_COMMAND_UNCHECKOUT對應於[SccUncheck。](../extensibility/sccuncheckout-function.md)

SCC_COMMAND_ADD對應於[SccAdd](../extensibility/sccadd-function.md)。

SCC_COMMAND_REMOVE對應於[SccRemove](../extensibility/sccremove-function.md)。

SCC_COMMAND_DIFF對應於[SccDiff](../extensibility/sccdiff-function.md)。

SCC_COMMAND_HISTORY對應於[史抄](../extensibility/scchistory-function.md)

SCC_COMMAND_RENAME對應於[SccRename](../extensibility/sccrename-function.md)。

SCC_COMMAND_PROPERTIES對應於[Scc 屬性](../extensibility/sccproperties-function.md)。

SCC_COMMAND_OPTIONS對應於[SccSetOption](../extensibility/sccsetoption-function.md)。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
