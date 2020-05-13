---
title: SccQuery資訊功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700484"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函式
此函數獲取原始程式碼管理下的一組選定檔的狀態資訊。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 n 檔案

[在]`lpFileNames`陣列中指定的檔案數和`lpStatus`陣列的長度。

 lpFile 名稱

[在]要查詢的檔的名稱陣列。

 lp狀態

[進出]源控元件外掛程式返回每個檔的狀態標誌的陣列。 有關詳細資訊,請參考[檔案狀態代碼](../extensibility/file-status-code-enumerator.md)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢成功。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由網路或爭用問題引起的。 建議重試。|
|SCC_E_PROJNOTOPEN|專案在原始程式碼管理下不開放。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 如果是`lpFileName`空字串,則當前沒有要更新的狀態資訊。 否則,它是狀態資訊可能已更改的檔的完整路徑名稱。

 返回陣列可以是`SCC_STATUS_xxxx`位掩碼。 有關詳細資訊,請參考[檔案狀態代碼](../extensibility/file-status-code-enumerator.md)。 原始程式碼管理系統可能不支援所有位類型。 例如,如果未`SCC_STATUS_OUTOFDATE`提供,則僅設置位。

 使用此函數簽出檔案時,請注意以下`MSSCCI`狀態要求:

- `SCC_STATUS_OUTBYUSER`當前使用者簽出檔時設置。

- `SCC_STATUS_CHECKEDOUT`除非已設定,`SCC_STATUS_OUTBYUSER`否則無法設定。

- `SCC_STATUS_CHECKEDOUT`僅在檔簽出到指定的工作目錄中時設置。

- 如果目前使用者將檔簽到工作目錄以外的目錄中,`SCC_STATUS_OUTBYUSER`則設置為未`SCC_STATUS_CHECKEDOUT`設置。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [檔案狀態碼](../extensibility/file-status-code-enumerator.md)
