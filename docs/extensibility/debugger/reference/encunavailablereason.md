---
title: EncUnavailableReason |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db94a181d87791edb242d69b461f90c42a5e080
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318150"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 表示的原因，**編輯後繼續**不提供。

## <a name="syntax"></a>語法

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
沒有特定的理由為何無法使用 編輯後繼續。

`ENCUN_INTEROP`\
編輯後繼續不提供 InterOp 呼叫期間。

`ENCUN_SQLCLR`\
編輯後繼續提供期間不會使用 Common Language Runtime (CLR) 的 SQL 程序呼叫。

`ENCUN_MINIDUMP`\
編輯後繼續不提供在處理小型傾印。

`ENCUN_EMBEDDED`\
編輯後繼續使用時不處理內嵌程式碼。

`ENCUN_ATTACH`\
編輯後繼續 無法使用工作階段已附加到，因為無法啟動的偵錯工具。

`ENCUN_WIN64`\
編輯後繼續不提供處理 64 位元 Windows 程式碼時。

## <a name="remarks"></a>備註
這個列舉僅供內部使用由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)並[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法所實作的自訂連接埠供應商應該一律會傳回`E_NOTIMPL`。

## <a name="requirements"></a>需求
標頭： msdbg.idl

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
