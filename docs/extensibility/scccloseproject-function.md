---
title: SccCloseProject 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333937"
---
# <a name="scccloseproject-function"></a>SccCloseProject 函式
此函式會關閉專案時，標示特定的工作階段結束。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>參數
 pvContext 原始檔控制外掛程式的內容結構。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功關閉專案。|
|SCC_E_PROJNOTOPEN|沒有任何專案目前開啟。|
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 [SccOpenProject](../extensibility/sccopenproject-function.md)一定會呼叫此函式前面。 呼叫此函式接下來是呼叫`SccOpenProject`函式或[SccUninitialize](../extensibility/sccuninitialize-function.md)，完全結束原始檔控制系統的連線。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)