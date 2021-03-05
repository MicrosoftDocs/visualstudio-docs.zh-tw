---
description: 指定要針對堆疊框架物件取得的資訊。
title: FRAMEINFO_FLAGS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4029212aae6d4557e17c42a0c0e024a83c94b0a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150818"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
指定要針對堆疊框架物件取得的資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>欄位
`FIF_FUNCNAME`\
初始化/使用 `m_bstrFuncName` 欄位。

`FIF_RETURNTYPE`\
初始化/使用 `m_bstrReturnType` 欄位。

`FIF_ARGS`\
初始化/使用 `m_bstrArgs` 欄位。

`FIF_LANGUAGE`\
初始化/使用 `m_bstrLanguage` 欄位。

`FIF_MODULE`\
初始化/使用 `m_bstrModule` 欄位。

`FIF_STACKRANGE`\
初始化/使用 `m_addrMin` 和 `m_addrMax` (堆疊範圍) 欄位。

`FIF_FRAME`\
初始化/使用 `m_pFrame` 欄位。

`FIF_DEBUGINFO`\
初始化/使用 `m_fHasDebugInfo` 欄位。

`FIF_STALECODE`\
初始化/使用 `m_fStaleCode` 欄位。

`FIF_ANNOTATEDFRAME`\
初始化/使用 `m_fAnnotatedFrame` 欄位。

`FIF_DEBUG_MODULEP`\
初始化/使用 `m_pModule` 欄位。

`FIF_FUNCNAME_FORMAT`\
將函數名稱格式化。 結果會在欄位中傳回 `m_bstrFunName` ，而且不會填寫任何其他欄位。

`FIF_FUNCNAME_RETURNTYPE`\
將傳回類型加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_ARGS`\
將引數加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_LANGUAGE`\
將語言新增至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_MODULE`\
將模組名稱加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_LINES`\
將行數加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_OFFSET`\
`m_bstrFuncName`如果 `FIF_FUNCNAME_LINES` 指定了，就會將從該行開頭算起的位移（以位元組為單位）加入至欄位。 如果未 `FIF_FUNCNAME_LINES` 指定，或如果行號無法使用，則會從函式的開頭處加上位元組位移。

`FIF_FUNCNAME_ARGS_TYPES`\
將每個函數引數的類型加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_ARGS_NAMES`\
將每個函數引數的名稱加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_ARGS_VALUES`\
將每個函數引數的值加入至 `m_bstrFuncName` 欄位。

`FIF_FUNCNAME_ARGS_ALL`\
將所有引數的類型、名稱和值加入至 `m_bstrFuncName` 欄位。

`FIF_ARGS_TYPES`\
引數類型會被抓取並格式化。

`FIF_ARGS_NAMES`\
引數名稱會被抓取並格式化。

`FIF_ARGS_VALUES`\
引數值會被取出並格式化。

`FIF_ARGS_ALL`\
取出並格式化所有引數的類型、名稱和值。

`FIF_ARGS_NOFORMAT`\
指定不將引數格式化 (例如，請勿在引數清單前後加上左括弧和右括弧，也不會在引數) 之間加入分隔符號。

`FIF_ARGS_NO_FUNC_EVAL`\
指定在抓取引數值時，不應該使用函數 (屬性) 評估。

`FIF_FILTER_NON_USER_CODE`\
偵錯工具引擎是篩選非使用者程式碼框架，因此不包含它們。

`FIF_ARGS_NO_TOSTRING`\
傳回函式 `ToString()` 引數時，不允許函數評估或格式化。

`FIF_DESIGN_TIME_EXPR_EVAL`\
畫面格資訊應從託管的應用程式網域取得，而不是從裝載進程取得。

## <a name="remarks"></a>備註
這些旗標會傳遞至 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 和 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 方法，以指出哪些欄位要在 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構或結構中初始化。

這些旗標也可用來指出當傳回結構時，所使用的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構欄位和有效的欄位。 這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
