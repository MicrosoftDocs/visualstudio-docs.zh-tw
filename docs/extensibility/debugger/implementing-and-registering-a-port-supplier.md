---
title: 執行和註冊埠供應商 |Microsoft Docs
description: 瞭解如何執行和註冊通訊埠供應商，以追蹤和提供管理進程的埠。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5639c45fd6dff6702ebc197d46c2eafe482e1d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926364"
---
# <a name="implement-and-register-a-port-supplier"></a>執行並註冊埠供應商
埠供應商的角色是追蹤和提供埠，進而管理進程。 當需要建立埠時，會使用 CoCreate 搭配埠供應商的 GUID 來具現化埠供應商 (會話 debug manager [SDM] 將使用使用者選取的埠供應商或專案系統所指定的埠供應商) 。 SDM 接著會呼叫 [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) ，以查看是否可以加入任何埠。 如果可以新增埠，則會藉由呼叫 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 來要求新的埠，並將描述該埠的 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 傳遞給它。 `AddPort` 傳回 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 介面所代表的新埠。

## <a name="discussion"></a>討論
 埠是由與電腦或 debug server 相關聯的埠供應商所建立。 伺服器會透過[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 方法列舉其埠供應商，而埠供應商會透過 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 方法列舉其埠。

 除了一般的 COM 註冊之外，埠供應商必須將其 CLSID 和名稱放在特定的登錄位置，以向 Visual Studio 註冊本身。 偵測到的偵錯工具 SDK helper 函式 `SetMetric` 會處理這個麻煩：每個要註冊的專案都會呼叫一次，因此：

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

 埠供應商藉由呼叫 (另一個偵錯工具協助程式函式來取消 `RemoveMetric` 註冊，以針對每個已註冊的專案) 一次，因此：

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
> [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` 和在 `RemoveMetric` *dbgmetric* 中定義的靜態函式，並編譯成 *ad2de .lib*。 `metrictypePortSupplier`、 `metricCLSID` 和協助程式 `metricName` 也會在 *dbgmetric* 中定義。

 埠供應商可以分別透過 [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) 和 [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)方法提供其名稱和 GUID。

## <a name="see-also"></a>另請參閱
- [執行埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)
- [用於偵錯工具的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [埠供應商](../../extensibility/debugger/port-suppliers.md)
