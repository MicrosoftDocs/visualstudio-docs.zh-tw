---
description: 此函式會取得原始檔控制下的一組選定檔案的狀態資訊。
title: SccQueryInfo 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 911219605859025f1877d040b5932714b10f836a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073894"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函式
此函式會取得原始檔控制下的一組選定檔案的狀態資訊。

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

在原始檔控制外掛程式內容結構。

 nFiles

在陣列中指定的檔案數目 `lpFileNames` 以及陣列的長度 `lpStatus` 。

 lpFileNames

在要查詢之檔案的名稱陣列。

 lpStatus

[in，out]陣列，其中的原始檔控制外掛程式會傳回每個檔案的狀態旗標。 如需詳細資訊，請參閱檔案 [狀態碼](../extensibility/file-status-code-enumerator.md)。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢成功。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題所致。 建議您重試。|
|SCC_E_PROJNOTOPEN|專案未在原始檔控制中開啟。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 如果 `lpFileName` 是空字串，目前沒有可更新的狀態資訊。 否則，它會是狀態資訊可能已變更之檔案的完整路徑名稱。

 傳回陣列可以是位的位元遮罩 `SCC_STATUS_xxxx` 。 如需詳細資訊，請參閱檔案 [狀態碼](../extensibility/file-status-code-enumerator.md)。 原始檔控制系統可能不支援所有的位類型。 例如，如果 `SCC_STATUS_OUTOFDATE` 未提供，則只會設定位。

 使用此函數簽出檔案時，請注意下列 `MSSCCI` 狀態需求：

- `SCC_STATUS_OUTBYUSER` 當目前使用者簽出檔案時設定。

- `SCC_STATUS_CHECKEDOUT` 除非 `SCC_STATUS_OUTBYUSER` 已設定，否則無法設定。

- `SCC_STATUS_CHECKEDOUT` 只有當檔案簽出至指定的工作目錄時，才會設定。

- 如果目前使用者將檔案簽出至工作目錄以外的目錄， `SCC_STATUS_OUTBYUSER` 則會設定但不是 `SCC_STATUS_CHECKEDOUT` 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [檔案狀態碼](../extensibility/file-status-code-enumerator.md)
