---
description: 表示無法使用 [編輯後繼續] 的原因。
title: EncUnavailableReason |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1f80dc1454cb1c15feddd099411bcb339dbc58c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151000"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 表示無法使用 [ **編輯後繼續** ] 的原因。

## <a name="syntax"></a>Syntax

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>欄位
`ENCUN_NONE`\
無法使用 [編輯後繼續] 的特定原因。

`ENCUN_INTEROP`\
在 InterOp 呼叫期間無法使用 [編輯後繼續]。

`ENCUN_SQLCLR`\
使用 Common Language Runtime (CLR) 的 SQL 程序呼叫期間，無法使用 [編輯後繼續]。

`ENCUN_MINIDUMP`\
處理迷你傾印時，無法使用 [編輯後繼續]。

`ENCUN_EMBEDDED`\
處理內嵌程式碼時，無法使用 [編輯後繼續]。

`ENCUN_ATTACH`\
無法使用 [編輯後繼續]，因為會話已附加至偵錯工具，而不是由偵錯工具所啟動。

`ENCUN_WIN64`\
處理64位 Windows 程式碼時，無法使用 [編輯後繼續]。

## <a name="remarks"></a>備註
這個列舉僅供內部使用 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。 自訂埠供應商所執行的 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 和 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 方法應該一律會傳回 `E_NOTIMPL` 。

## <a name="requirements"></a>規格需求
標頭： msdbg .idl

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
