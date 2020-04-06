---
title: Enc不可用原因 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737165"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`表示 **「編輯」和「繼續」** 不可用的原因。

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
沒有"編輯並繼續"不可用的具體原因。

`ENCUN_INTEROP`\
在互通話務期間,編輯和繼續不可用。

`ENCUN_SQLCLR`\
在使用通用語言運行時 (CLR) 的 SQL 過程調用期間,編輯和繼續不可用。

`ENCUN_MINIDUMP`\
處理小型轉儲時,編輯和繼續不可用。

`ENCUN_EMBEDDED`\
處理嵌入的代碼時,編輯和繼續不可用。

`ENCUN_ATTACH`\
編輯和繼續不可用,因為會話已附加到調試器,而不是由調試器啟動。

`ENCUN_WIN64`\
在處理 64 位 Windows 代碼時,編輯和繼續不可用。

## <a name="remarks"></a>備註
此枚舉僅供[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]內部使用。 自訂埠供應商實現的[GetENC 可用狀態](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)與[關閉 ENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法`E_NOTIMPL`應傳回 。

## <a name="requirements"></a>需求
標題: msdbg.idl

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
