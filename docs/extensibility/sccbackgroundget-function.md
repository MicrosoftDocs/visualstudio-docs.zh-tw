---
title: SccBackgroundGet 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e1768e23eb61a5a6463d8d48f64683987f431a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707964"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 函式
此函式會擷取從原始檔控制每個指定的檔案而不需要使用者互動。

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

[in]原始檔控制外掛程式的內容指標。

 nFiles

[in]中指定的檔案數目`lpFileNames`陣列。

 lpFileNames

[in、 out]要擷取的檔案名稱的陣列。

> [!NOTE]
>  名稱必須是完整的本機檔案名稱。

 dwFlags

[in]命令旗標 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。

 dwBackgroundOperationID

[in]這項作業相關聯的唯一值。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|作業已順利完成。|
|SCC_E_BACKGROUNDGETINPROGRESS|背景擷取已正在的進行 （原始檔控制外掛程式應該傳回這才是它不支援同時批次作業）。|
|SCC_I_OPERATIONCANCELED|在完成前已取消作業。|

## <a name="remarks"></a>備註
 不同於載入原始檔控制外掛程式的另一個執行緒上，一律會呼叫此函數。 此函式不應該傳回之前完成;不過，它可以與多個清單的檔案，所有同時呼叫多次。

 善用`dwFlags`引數是相同[SccGet](../extensibility/sccget-function.md)。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)