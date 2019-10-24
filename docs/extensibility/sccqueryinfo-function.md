---
title: SccQueryInfo 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720836"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函式
此函式會取得原始檔控制下一組所選檔案的狀態資訊。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 n

在@No__t_0 陣列中指定的檔案數目和 `lpStatus` 陣列的長度。

 lpFileNames

在要查詢之檔案的名稱陣列。

 lpStatus

[in、out]一種陣列，原始檔控制外掛程式會在其中傳回每個檔案的狀態旗標。 如需詳細資訊，請參閱檔案[狀態碼](../extensibility/file-status-code-enumerator.md)。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢成功。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題所造成。 建議使用重試。|
|SCC_E_PROJNOTOPEN|專案未在原始檔控制下開啟。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 如果 `lpFileName` 是空字串，目前沒有要更新的狀態資訊。 否則，它是狀態資訊可能已變更之檔案的完整路徑名稱。

 傳回陣列可以是 `SCC_STATUS_xxxx` 位的位元遮罩。 如需詳細資訊，請參閱檔案[狀態碼](../extensibility/file-status-code-enumerator.md)。 原始檔控制系統可能不支援所有的位類型。 例如，如果未提供 `SCC_STATUS_OUTOFDATE`，則只會設定位。

 使用此函數來簽出檔案時，請注意下列 `MSSCCI` 狀態需求：

- 當目前的使用者簽出檔案時，就會設定 `SCC_STATUS_OUTBYUSER`。

- 除非已設定 `SCC_STATUS_OUTBYUSER`，否則無法設定 `SCC_STATUS_CHECKEDOUT`。

- 只有在檔案簽出至指定的工作目錄時，才會設定 `SCC_STATUS_CHECKEDOUT`。

- 如果目前的使用者將檔案簽出至工作目錄以外的目錄，則 `SCC_STATUS_OUTBYUSER` 已設定，但 `SCC_STATUS_CHECKEDOUT` 不是。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [檔案狀態碼](../extensibility/file-status-code-enumerator.md)