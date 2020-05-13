---
title: Scc 解初始化功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700235"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 函式
此功能清理以前調用[Scc初始化](../extensibility/sccinitialize-function.md)創建的任何分配或打開連接,以準備關閉原始程式碼管理外掛程式。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]指向在[Scc 初始化](../extensibility/sccinitialize-function.md)中創建的原始程式碼管理外掛程式上下文結構的指標。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|清理工作成功完成。|

## <a name="remarks"></a>備註
 原始程式碼管理外掛程式負責準備關閉和釋放外掛程式為上下文結構分配的記憶體。 對於外掛程式的每個給定實例,該函數調用一次。 在此調用之前,對[Scc 初始化的](../extensibility/sccinitialize-function.md)調用。 呼叫 時無法開啟任何項目`SccUninitialize`。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
