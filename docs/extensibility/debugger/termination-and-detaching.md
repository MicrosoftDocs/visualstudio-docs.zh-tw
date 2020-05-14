---
title: 終止與分離 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712485"
---
# <a name="termination-and-detaching"></a>終止與分離
以下部分介紹正常終止。

## <a name="discussion"></a>討論區
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)介面繼續後,如果要調試的應用程式中沒有斷點、異常、運行時錯誤或無限迴圈,則正在調試的程式將運行到完成。 此過程是正常的終止。

 您必須發送[IDebugProgram 銷毀事件2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)來實現正常終止。 正常終止需要運行[IDebugProgram銷毀事件2::getExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)方法。

## <a name="see-also"></a>另請參閱
- [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
