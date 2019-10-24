---
title: SccUncheckout 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35d7287d8fc12100da9ba3b8383d8e92cee73d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720537"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函式
此函式會復原先前的簽出作業，藉此將選取的檔案內容還原到簽出之前的狀態。 自簽出後對檔案所做的所有變更都會遺失。

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

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 n

在@No__t_0 陣列中指定的檔案數目。

 lpFileNames

在要復原簽出之檔案的完整本機路徑名稱陣列。

 fOptions

在命令旗標（未使用）。

 pvOptions

在原始檔控制外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|復原簽出成功。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始碼控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。 建議使用重試。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。 復原簽出失敗。|
|SCC_E_NOTCHECKEDOUT|使用者沒有簽出的檔案。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此作業。|
|SCC_E_PROJNOTOPEN|尚未從原始檔控制開啟專案。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|

## <a name="remarks"></a>備註
 在這項作業之後，將會針對執行復原簽出的檔案清除 `SCC_STATUS_CHECKEDOUT` 和 `SCC_STATUS_MODIFIED` 旗標。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)