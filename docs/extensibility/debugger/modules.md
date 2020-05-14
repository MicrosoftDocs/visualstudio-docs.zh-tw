---
title: 模組 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738342"
---
# <a name="modules"></a>模組
在除錯器架構結構方面,*模組*:

- 是代碼的物理容器,如可執行檔或 DLL。

- 可以重新載入其符號並描述自身。 模組說明顯示在 IDE 的「模組」視窗中。

- 由[IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)介面表示,該介面由調試引擎創建,用於描述模組。

## <a name="see-also"></a>另請參閱
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
