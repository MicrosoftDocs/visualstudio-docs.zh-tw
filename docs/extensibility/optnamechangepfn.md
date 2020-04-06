---
title: OPTNAMECHANGEPFN |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702241"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
這是一個回調函數,在調用[SccSetOption(](../extensibility/sccsetoption-function.md)`SCC_OPT_NAMECHANGEPFN`使用選項 )中指定,用於將原始程式碼管理外掛程式所做的名稱更改傳回 IDE。

## <a name="signature"></a>簽章

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>參數
 pvCallerData

[在]在以前調用[SccSetOption](../extensibility/sccsetoption-function.md)時指定的使用者值`SCC_OPT_USERDATA`(使用選項)。

 pszOld名稱

[在]檔的原始名稱。

 psnewName

[在]檔案重新命名為的名稱。

## <a name="return-value"></a>傳回值
 無。

## <a name="remarks"></a>備註
 如果在原始程式碼管理操作期間重新命名了檔,原始程式可以透過此回檔通知 IDE 有關名稱更改。

 如果 IDE 不支援此回調,則不會調用[SccSetOption](../extensibility/sccsetoption-function.md)來指定它。 如果外掛程式不支援此回調,則當 IDE 嘗試`SCC_E_OPNOTSUPPORTED`設置回調時`SccSetOption`,它將從函數返回。

## <a name="see-also"></a>另請參閱
- [IDE 實作的回檔](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
