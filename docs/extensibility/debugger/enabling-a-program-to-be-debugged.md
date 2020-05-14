---
title: 使程式被除錯 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738888"
---
# <a name="enable-a-program-to-be-debugged"></a>開啟對程式進行除錯
在除錯引擎 (DE) 可以除錯程式之前,必須首先啟動 DE 或將其附加到現有程式。

## <a name="in-this-section"></a>本節內容
 [取得連接埠](../../extensibility/debugger/getting-a-port.md)討論如何獲取埠作為啟用程式調試的第一步。

 [註冊程式](../../extensibility/debugger/registering-the-program.md)解釋啟用程序調試的下一步:將其註冊到埠。 註冊后,可以通過附加或及時 (JIT) 調試過程對程序進行調試。

 [附加到程式](../../extensibility/debugger/attaching-to-the-program.md)解釋下一步:將調試器附加到程式。

 [建基於啟動的附加](../../extensibility/debugger/launch-based-attachment.md)描述程式基於啟動的附件,SDM 在啟動時自動進行該附件。

 [傳送所需事件](../../extensibility/debugger/sending-the-required-events.md)在創建除錯引擎 (DE) 並將其附加到程式時,執行所需的事件。

## <a name="related-sections"></a>相關章節
 [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)定義調試引擎 (DE),並描述通過 DE 介面實現的服務,以及它們如何導致調試器在不同操作模式之間轉換。
