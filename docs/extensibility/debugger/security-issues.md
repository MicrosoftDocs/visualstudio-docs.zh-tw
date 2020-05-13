---
title: 安全問題 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713056"
---
# <a name="security-issues"></a>安全性問題
要使用 Visual Studio 調試程式,所需的唯一許可權與開發人員運行程式所需的許可權相同。 這包括大多數情況下的遠端調試。 某些涉及其他服務(如 Internet 資訊服務)的情況可能需要更高級別的許可權。

 當 Visual Studio 執行時,行程除錯管理員 (PDM) 追蹤本地電腦上的調試過程。 開發人員遠端啟動名為*msvsmon.exe*的程式,以處理遠端除錯並使 PDM 可用。 *(msvsmon.exe*不是服務,必須手動啟動才能在該電腦上啟用遠端調試。當 Visual Studio (或*msvsmon.exe*) 未執行時,不會追蹤任何進程以進行調試。

 開發人員可以調試他們啟動的程式,無需特殊許可權。 如果其他人是同一安全組的成員,開發人員甚至可以調試由其他人啟動的進程。 而且,為了啟用遠端調試,只需將所需的檔案複製到遠端電腦並啟動*msvsmon.exe。* 有關詳細資訊,請參閱[遠端除錯](../../debugger/remote-debugging.md)。

## <a name="see-also"></a>另請參閱
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
- [程序除錯管理員](../../extensibility/debugger/process-debug-manager.md)
- [遠端偵錯](../../debugger/remote-debugging.md)
