---
title: FRAMEINFO_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736804"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
指定要檢索有關堆疊幀物件的資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_FRAMEINFO_FLAGS {
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
public enum enum_FRAMEINFO_FLAGS {
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
初始化/使用`m_bstrFuncName`欄位。

`FIF_RETURNTYPE`\
初始化/使用`m_bstrReturnType`欄位。

`FIF_ARGS`\
初始化/使用`m_bstrArgs`欄位。

`FIF_LANGUAGE`\
初始化/使用`m_bstrLanguage`欄位。

`FIF_MODULE`\
初始化/使用`m_bstrModule`欄位。

`FIF_STACKRANGE`\
初始化/使用`m_addrMin``m_addrMax`和堆疊範圍) 欄位。

`FIF_FRAME`\
初始化/使用`m_pFrame`欄位。

`FIF_DEBUGINFO`\
初始化/使用`m_fHasDebugInfo`欄位。

`FIF_STALECODE`\
初始化/使用`m_fStaleCode`欄位。

`FIF_ANNOTATEDFRAME`\
初始化/使用`m_fAnnotatedFrame`欄位。

`FIF_DEBUG_MODULEP`\
初始化/使用`m_pModule`欄位。

`FIF_FUNCNAME_FORMAT`\
設定函數名稱的格式。 結果在欄位中傳回`m_bstrFunName`, 並且不會填寫其他欄位。

`FIF_FUNCNAME_RETURNTYPE`\
將返回類型添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_ARGS`\
將參數添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_LANGUAGE`\
將語言添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_MODULE`\
將模組名稱添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_LINES`\
將行數添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_OFFSET`\
如果`FIF_FUNCNAME_LINES`指定,`m_bstrFuncName`則從行的開頭向欄位添加偏移量(以位元組為單位)。 如果未`FIF_FUNCNAME_LINES`指定,或者如果行號不可用,則從函數的開頭添加偏移以位元組為單位。

`FIF_FUNCNAME_ARGS_TYPES`\
將每個函數參數的類型添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_ARGS_NAMES`\
將每個函數參數的名稱添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_ARGS_VALUES`\
將每個函數參數的值添加到`m_bstrFuncName`欄位中。

`FIF_FUNCNAME_ARGS_ALL`\
將所有參數的類型、名稱和值添加到`m_bstrFuncName`欄位中。

`FIF_ARGS_TYPES`\
將檢索參數類型並設置格式。

`FIF_ARGS_NAMES`\
檢索參數名稱並設置格式。

`FIF_ARGS_VALUES`\
將檢索參數值並設置格式。

`FIF_ARGS_ALL`\
檢索並格式化所有參數的類型、名稱和值。

`FIF_ARGS_NOFORMAT`\
指定不格式化參數(例如,不要在參數列表周圍添加首和閉括弧,也不在參數之間添加分隔符)。

`FIF_ARGS_NO_FUNC_EVAL`\
指定在檢索參數值時不應使用函數(屬性)計算。

`FIF_FILTER_NON_USER_CODE`\
調試引擎是篩選非用戶代碼幀,以便不包含這些幀。

`FIF_ARGS_NO_TOSTRING`\
傳回函數`ToString()`參數 時不允許函數計算或格式化。

`FIF_DESIGN_TIME_EXPR_EVAL`\
幀資訊應從託管應用域(而不是託管進程)獲取。

## <a name="remarks"></a>備註
這些標誌將傳遞給[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)和[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法,以指示要在[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構或結構中初始化哪些欄位。

這些標誌還用於指示在返回結構時使用[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構的哪些欄位並有效。 這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
