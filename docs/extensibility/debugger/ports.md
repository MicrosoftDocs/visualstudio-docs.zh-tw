---
title: 埠 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738314"
---
# <a name="ports"></a>連接埠
在除錯器架構結構中,*連接埠*:

- 是伺服器上運行的一組進程的容器。 例如,埠可能透過串列電纜或網路非 DCOM 電腦表示與基於 Windows CE 的裝置的連接。 一個稱為本地埠的特殊埠包含在本地電腦上運行的所有進程。

- 可以按名稱或標識符標識自身。

- 可以枚舉在埠上運行的所有進程,並啟動和終止這些進程。

- 由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面表示,該介面通過將[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)參數傳遞給[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)創建。

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供預設埠,用於處理所有基於 Windows 的進程,包括本機進程和託管進程。 必須為與非基於 Windows 的外部裝置的連接設置自訂埠。 要提供此類自定義埠,還必須設置自定義埠供應商。

## <a name="see-also"></a>另請參閱
- [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [過程](../../extensibility/debugger/processes.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
