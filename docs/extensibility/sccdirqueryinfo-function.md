---
description: 此函式會檢查完整目錄的清單，以取得其目前的狀態。
title: SccDirQueryInfo 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81087d4f4da3435fb7bc80ec4a965394c7d6c7f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060324"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 函式
此函式會檢查完整目錄的清單，以取得其目前的狀態。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容結構。

 nDirs

在選取要查詢的目錄數目。

 lpDirNames

在要查詢之目錄的完整路徑陣列。

 lpStatus

[in，out]原始檔控制外掛程式的陣列結構，用來傳回狀態旗標 (如需詳細資料，請參閱 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢成功。|
|SCC_E_OPNOTSUPPORTED|原始程式碼控制系統不支援這種操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|模糊失敗。|

## <a name="remarks"></a>備註
 函式會使用系列中的位位元遮罩來填滿 `SCC_DIRSTATUS` 傳回陣列 (查看 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)) ，為每個指定的目錄輸入一個專案。 狀態陣列是由呼叫端配置。

 在目錄重新命名之前，IDE 會使用這個函式，藉由查詢是否有對應的專案來檢查目錄是否在原始檔控制之下。 如果目錄不在原始檔控制之下，IDE 可以為使用者提供適當的警告。

> [!NOTE]
> 如果原始檔控制外掛程式選擇不執行一或多個狀態值，則未完成的位應設定為零。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)
