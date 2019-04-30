---
title: SccHistory 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d84de96181018858515bd74156f844ed6022f0a9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434618"
---
# <a name="scchistory-function"></a>SccHistory 函式
此函式會顯示指定的檔案歷程記錄。

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

[in]原始檔控制外掛程式的內容結構。

 `hWnd`

[in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。

 `nFiles`

[in]中指定的檔案數目`lpFileName`陣列。

 `lpFileName`

[in]檔案的完整名稱的陣列。

 `fOptions`

[in]（目前未使用） 的命令旗標。

 `pvOptions`

[in]原始檔控制外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功取得版本歷程記錄。|
|SCC_I_RELOADFILE|原始檔控制系統實際修改磁碟上的檔案時擷取歷程記錄 （比方說，藉由取得它的舊版本），讓 IDE 應重新載入這個檔案。|
|SCC_E_FILENOTCONTROLLED|檔案不是原始檔控制之下。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|
|SCC_E_PROJNOTOPEN|專案已開啟。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。 無法取得檔案歷程記錄。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式可以顯示自己的對話方塊，以顯示每個檔案的歷程記錄使用`hWnd`與父視窗。 或者，選擇性的文字輸出回呼函式提供給[SccOpenProject](../extensibility/sccopenproject-function.md)可用，如果它受支援。

 請注意，在某些情況下，此呼叫的執行期間可能會變更所檢查的檔案。 比方說，[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]歷程記錄命令讓使用者有機會取得舊版本的檔案。 在此情況下，原始檔控制外掛程式傳回`SCC_I_RELOAD`警告 IDE，它需要重新載入檔案。

> [!NOTE]
> 如果原始檔控制外掛程式不支援此函式陣列的檔案，就可以顯示只有第一個檔案的檔案歷程記錄。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)