---
title: EncUnavailableReason |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717035"
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

#### <a name="parameters"></a>參數
為何無法使用 編輯後繼續 ENCUN_NONE 否的特定原因。

ENCUN_INTEROP 編輯後繼續不提供 InterOp 呼叫期間。

ENCUN_SQLCLR 編輯後繼續提供期間不會使用 Common Language Runtime (CLR) 的 SQL 程序呼叫。

ENCUN_MINIDUMP 編輯後繼續不提供在處理小型傾印。

ENCUN_EMBEDDED 編輯後繼續使用時不處理內嵌程式碼。

ENCUN_ATTACH 編輯後繼續不提供工作階段已附加到，因為未啟動的偵錯工具。

ENCUN_WIN64 編輯後繼續不提供處理 64 位元 Windows 程式碼時。

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
