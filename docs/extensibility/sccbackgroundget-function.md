---
title: Scc背景取得功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701236"
---
# <a name="sccbackgroundget-function"></a>Scc背景抓取功能
此函數從原始程式碼管理檢索每個指定的檔,而沒有使用者互動。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>參數
 pContext

[在]源代碼管理外掛程式上下文指標。

 n 檔案

[在]`lpFileNames`陣列中指定的檔案數。

 lpFile 名稱

[進出]要檢索的文件的名稱陣列。

> [!NOTE]
> 名稱必須是完全限定的本地檔名。

 dwFlags

[在]命令標誌`SCC_GET_ALL`(。 `SCC_GET_RECURSIVE`

 dw背景操作ID

[在]與此操作關聯的唯一值。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|作業順利完成。|
|SCC_E_BACKGROUNDGETINPROGRESS|後台檢索已在進行中(原始程式碼管理外掛程式應僅當它不支援同時批處理操作時才返回它)。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|

## <a name="remarks"></a>備註
 此函數始終調用與載入原始程式碼管理外掛程式不同的線程。 在完成之前,不應返回此功能;但是,它可以調用多個檔清單,同時調用。

 參數的使用`dwFlags`與[SccGet](../extensibility/sccget-function.md)相同。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
