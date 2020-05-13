---
title: 實施和註冊港口供應商 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738528"
---
# <a name="implement-and-register-a-port-supplier"></a>實施和註冊埠供應商
埠供應商的作用是跟蹤和供應埠,而埠又管理流程。 當需要創建埠時,將使用 CoCreate 與埠供應商的 GUID 實例化埠供應商(工作階段調試管理器 [SDM] 將使用使用者選擇的埠供應商或專案系統指定的埠供應商)。 然後,SDM 調用[CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)以查看是否可以添加任何埠。 如果可以添加埠,則透過調用[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)並傳遞描述該埠的[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)來請求新埠。 `AddPort`返回由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面表示的新埠。

## <a name="discussion"></a>討論區
 埠由與計算機或調試伺服器關聯的埠供應商創建。 伺服器通過[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)方法枚舉其埠供應商,埠供應商通過[枚舉埠](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)方法枚舉其埠。

 除了典型的 COM 註冊之外,埠供應商還必須將其 CLSID 和名稱放在特定的註冊表位置,從而在 Visual Studio 中註冊。 呼叫`SetMetric`的除錯 SDK 說明器函數處理此雜務:為要註冊的每個項目呼叫一次,因此:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 連接埠供應商透過呼叫`RemoveMetric`(另一個除錯 SDK 說明器函數)對已註冊的每個專案一次來取消註冊自身,從而:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> [除錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetMetric`的 SDK`RemoveMetric`說明器是*dbgmetric.h*中定義的靜態函數,並編譯為*ad2de.lib*。 和説明器也在*dbgmetric.h*中定義。`metrictypePortSupplier` `metricCLSID` `metricName`

 埠供應商可以通過[GetPort供應商名稱](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)和[GetPortSupplyId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)的方法分別提供其名稱和GUID。

## <a name="see-also"></a>另請參閱
- [實施埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)
- [除錯的 SDK 說明器](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [港口供應商](../../extensibility/debugger/port-suppliers.md)
