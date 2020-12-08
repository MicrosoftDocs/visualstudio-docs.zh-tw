---
title: 安全性問題 |Microsoft Docs
description: 瞭解使用 Visual Studio 來對程式進行偵錯工具所需的許可權，包括遠端偵錯程式以及牽涉到其他服務的情況。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 632150101b966e128e8a34636b01a369a1db5c64
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847607"
---
# <a name="security-issues"></a>安全性問題
若要使用 Visual Studio 來對程式進行偵錯工具，唯一需要的許可權，與開發人員執行程式所需的許可權相同。 這包括在大部分情況下進行遠端偵錯程式。 某些情況下，牽涉到其他服務（例如網際網路資訊服務）可能需要較高層級的許可權。

 當 Visual Studio 正在執行時，進程 debug manager (PDM) 會追蹤本機電腦上的偵錯工具。 從遠端開始，開發人員會啟動稱為 *msvsmon.exe* 的程式來處理遠端偵錯程式，並讓 PDM 可用。  (*msvsmon.exe* 不是服務，必須以手動方式啟動，才能在該電腦上啟用遠端偵錯程式。當 Visual Studio (或 *msvsmon.exe*) 未執行時，) 不會追蹤處理常式。

 開發人員可以將其啟動的程式與沒有特殊許可權的程式進行偵錯工具。 如果其他人是相同安全性群組的成員，開發人員甚至可以對其他人啟動的進程進行偵錯工具。 而且，若要啟用遠端偵錯程式，只需要將必要的檔案複製到遠端電腦，然後啟動 *msvsmon.exe*。 如需詳細資訊，請參閱 [遠端偵錯](../../debugger/remote-debugging.md)程式。

## <a name="see-also"></a>另請參閱
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
- [進程偵錯工具管理員](../../extensibility/debugger/process-debug-manager.md)
- [遠端偵錯](../../debugger/remote-debugging.md)
