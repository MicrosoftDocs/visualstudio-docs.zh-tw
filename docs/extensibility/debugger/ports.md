---
title: 埠 |Microsoft Docs
description: 本文說明 Visual Studio 中偵錯工具架構中的埠定義和角色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900768"
---
# <a name="ports"></a>連接埠
在偵錯工具架構中， *埠*：

- 是在伺服器上執行的一組進程的容器。 例如，埠可能代表透過序列纜線或網路非 DCOM 電腦連線到 Windows CE 型裝置。 一個特殊的埠（稱為本機埠）包含在本機電腦上執行的所有處理常式。

- 可以依名稱或識別碼來識別其本身。

- 可以列舉在埠上執行的所有處理常式，並啟動和終止這些進程。

- 是由 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 介面表示，它是藉由將 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 引數傳遞至 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)所建立。

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供預設的埠，可處理所有以 Windows 為基礎的處理常式，原生和受控。 您必須針對不是以 Windows 為基礎的外部裝置連接設定自訂埠。 若要提供這類自訂埠，您也必須設定自訂埠供應商。

## <a name="see-also"></a>另請參閱
- [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [處理序](../../extensibility/debugger/processes.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
