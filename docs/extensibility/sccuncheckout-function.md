---
title: SccUncheckout 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdcd8cd94914763d103a6232c4f87c3ec93f216
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836666"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函式
此函式會復原先前的簽出作業，藉此將所選取檔案的內容還原到簽出之前的狀態。 簽出之後對檔案所做的所有變更都會遺失。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在陣列中指定的檔案數目 `lpFileNames` 。

 lpFileNames

在要復原簽出之檔案的完整本機路徑名稱陣列。

 fOptions

在 (不使用) 的命令旗標。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|復原簽出成功。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始程式碼控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR|模糊失敗。 復原簽出失敗。|
|SCC_E_NOTCHECKEDOUT|使用者沒有簽出檔案。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_PROJNOTOPEN|尚未從原始檔控制中開啟專案。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|

## <a name="remarks"></a>備註
 在這項作業之後 `SCC_STATUS_CHECKEDOUT` ， `SCC_STATUS_MODIFIED` 會針對執行復原簽出的檔案清除和旗標。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
