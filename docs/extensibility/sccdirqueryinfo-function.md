---
title: SccDirQuery資訊功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700957"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 功能
此函數檢查完全限定的目錄的清單,以檢查其當前狀態。

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

[在]原始程式碼管理外掛程式上下文結構。

 nDirs

[在]選擇要查詢的目錄數。

 lpDirnames

[在]要查詢的目錄的完全限定路徑的陣列。

 lp狀態

[進出]源代碼管理外掛程式的陣列結構,用於返回狀態標誌(有關詳細資訊,請參閱[目錄狀態代碼](../extensibility/directory-status-code-enumerator.md))。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢成功。|
|SCC_E_OPNOTSUPPORTED|原始程式碼控制系統不支援此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特異性故障。|

## <a name="remarks"></a>備註
 函數用`SCC_DIRSTATUS`來自族的位掩碼填充返回陣列(請參閱[目錄狀態代碼](../extensibility/directory-status-code-enumerator.md)),每個目錄都有一個條目。 狀態數組由調用方分配。

 IDE 在重命名目錄之前使用此函數,通過查詢目錄是否具有相應的專案來檢查該目錄是否處於原始程式碼管理之下。 如果目錄不受原始程式碼管理,IDE可以向使用者提供適當的警告。

> [!NOTE]
> 如果原始程式碼管理外掛程式選擇不實現一個或多個狀態值,則應將未實現位設置為零。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [目錄狀態代碼](../extensibility/directory-status-code-enumerator.md)
