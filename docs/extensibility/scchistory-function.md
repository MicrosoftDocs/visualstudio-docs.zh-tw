---
description: 此函數會顯示指定檔案的歷程記錄。
title: SccHistory 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11a3056e34d15e2e04b687a518e86041dc270997
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063847"
---
# <a name="scchistory-function"></a>SccHistory 函式
此函數會顯示指定檔案的歷程記錄。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>參數
 `pvContext`

在原始檔控制外掛程式內容結構。

 `hWnd`

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 `nFiles`

在陣列中指定的檔案數目 `lpFileName` 。

 `lpFileName`

在檔案完整名稱的陣列。

 `fOptions`

在 (目前未使用) 的命令旗標。

 `pvOptions`

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功取得版本歷程記錄。|
|SCC_I_RELOADFILE|原始檔控制系統會在提取歷程記錄 (時，實際修改磁片上的檔案，方法是取得) 的舊版本，因此 IDE 應該重載此檔案。|
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制之下。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這種操作。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_PROJNOTOPEN|專案尚未開啟。|
|SCC_E_NONSPECIFICERROR|模糊失敗。 無法取得檔案歷程記錄。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式可以顯示自己的對話方塊，以顯示每個檔案的歷程記錄，並使用 `hWnd` 做為父視窗。 或者，如果支援的話，也可以使用提供給 [SccOpenProject](../extensibility/sccopenproject-function.md) 的選擇性文字輸出回撥函數。

 請注意，在某些情況下，所檢查的檔案可能會在此呼叫執行期間變更。 例如， [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] history 命令可讓使用者有機會取得檔案的舊版本。 在這種情況下，原始檔控制外掛程式會傳回， `SCC_I_RELOAD` 以警告 IDE 需要重載檔案。

> [!NOTE]
> 如果原始檔控制外掛程式不支援檔案陣列的這項功能，則只會顯示第一個檔案的檔案歷程記錄。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
