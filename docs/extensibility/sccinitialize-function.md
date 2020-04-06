---
title: 初始化功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700635"
---
# <a name="sccinitialize-function"></a>SccInitialize 函式
此功能初始化源代碼管理外掛程式,並為整合式開發環境 (IDE) 提供功能和限制。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>參數
 `ppvContext`

[在]源代碼管理外掛程式可以在此處放置指向其上下文結構的指標。

 `hWnd`

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 `lpCallerName`

[在]呼叫原始程式碼管理外掛程式的程式名稱。

 `lpSccName`

[進出]原始程式碼管理外掛程式放置其自己的名稱(`SCC_NAME_LEN`不要超過)的緩衝區。

 `lpSccCaps`

[出]返回原始程式碼管理外掛程式的功能標誌。

 `lpAuxPathLabel`

[進出]原始程式碼管理外掛程式放置一個字串,用於描述[SccOpenProject](../extensibility/sccopenproject-function.md)和[SccGetProjPath](../extensibility/sccgetprojpath-function.md)傳回的`SCC_AUXLABEL_LEN``lpAuxProjPath`參數(不要超過 )。

 `pnCheckoutCommentLen`

[出]返回結帳註釋的最大允許長度。

 `pnCommentLen`

[出]返回其他註釋的最大允許長度。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|原始程式碼管理初始化成功。|
|SCC_E_INITIALIZEFAILED|無法初始化系統。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行指定的操作。|
|SCC_E_NONSPECFICERROR|非特異性故障;源控制系統未初始化。|

## <a name="remarks"></a>備註
 IDE 首次載入原始程式碼管理外掛程式時調用此功能。 它使IDE能夠將某些資訊(如調用方名稱)傳遞給外掛程式。 IDE 還會返回某些資訊,例如註釋的最大允許長度和外掛程式的功能。

 指向`ppvContext`指標`NULL`。 源代碼管理外掛程式可以分配一個結構供自己使用,並在`ppvContext`中 存儲指向該結構的指標。 IDE 會將此指標傳遞給所有其他 VSSCI API 函數,允許外掛程式在不使用全域儲存的情況下提供上下文資訊,並支援外掛程式的多個實例。 調用[SccUn初始化](../extensibility/sccuninitialize-function.md)時,應處理此結構。

 和`lpCallerName``lpSccName`參數使IDE和原始程式碼管理外掛程式能夠交換名稱。 這些名稱可能僅用於區分多個實例,或者它們實際上可能顯示在菜單或對話框中。

 該`lpAuxPathLabel`參數是一個字串,用作註釋,用於識別存儲在解決方案檔中並傳遞到[SccOpenProject](../extensibility/sccopenproject-function.md)調用中的原始程式碼管理外掛程式的輔助專案路徑。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]使用字串「源安全專案:";其他原始程式碼管理外掛程式應避免使用此特定字串。

 該`lpSccCaps`參數為原始程式碼管理外掛程式提供了一個儲存指示外掛程式功能的位標誌的位置。 (有關功能位標誌的完整清單,請參閱[功能標誌](../extensibility/capability-flags.md))。 例如,如果外掛程式計畫將結果寫入調用方提供的回調函數,則外掛程式將SCC_CAP_TEXTOUT設置功能位。 這將發出 IDE 信號,為版本控制結果創建一個視窗。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [功能旗標](../extensibility/capability-flags.md)
