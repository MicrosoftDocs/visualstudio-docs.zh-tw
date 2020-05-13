---
title: 波普迪利斯芬奇 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702072"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
這是為[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)函數提供的回調函數,用於更新目錄和(可選)檔名的集合,以找出受原始程式碼管理。

 `POPDIRLISTFUNC`應僅對實際受原始程式碼管理的目錄和檔名(在提供`SccPopulateDirList`給函數的清單中)調用回調。

## <a name="signature"></a>簽章

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>參數
 pvCallerData

[在]提供[SccpopulateDirlist 的使用者](../extensibility/sccpopulatedirlist-function.md)值 。

 bFolder

[在]`TRUE`如果中`lpDirectoryOrFileName`的名稱是目錄;如果否則,名稱是檔名。

 lpDirectoryOr檔案名稱

[在]目錄或檔名的完整本地路徑,由原始程式碼控制。

## <a name="return-value"></a>傳回值
 IDE 傳回錯誤代碼:

|值|描述|
|-----------|-----------------|
|SCC_OK|繼續處理。|
|SCC_I_OPERATIONCANCELED|停止處理。|
|SCC_E_xxx|任何適當的原始程式碼管理錯誤都應停止處理。|

## <a name="remarks"></a>備註
 如果`fOptions``SccPopulateDirList`函數的參數`SCC_PDL_INCLUDEFILES`包含 標誌,則清單可能包含檔名和目錄名。

## <a name="see-also"></a>另請參閱
- [IDE 實作的回檔](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [錯誤碼](../extensibility/error-codes.md)
