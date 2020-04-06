---
title: SccRunScc 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700400"
---
# <a name="sccrunscc-function"></a>SccRunScc 函式
此函數調用原始程式碼管理工具。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]`lpFileNames`陣列中指定的檔案數。

 lpFile 名稱

[在]所選檔名的陣列。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功調用原始程式碼管理工具。|
|SCC_I_OPERATIONCANCELED|操作已取消。|
|SCC_E_INITIALIZEFAILED|無法初始化原始碼管理系統。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。|
|SCC_E_CONNECTIONFAILURE|無法連接到原始程式碼管理系統。|
|SCC_E_FILENOTCONTROLLED|所選檔不受原始程式碼管理。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 此功能允許調用方透過外部管理工具存取原始程式碼管理系統的全部功能。 如果原始程式碼管理系統沒有使用者介面,原始程式碼管理外掛程式可以實現一個介面來執行必要的管理功能。

 此函數使用當前選定檔的 count 和檔名陣列進行呼叫。 如果管理工具支援它,則檔案清單可用於在管理介面中預先選擇檔;如果管理工具支援它,則檔案清單可用於預先選擇管理介面中的檔。否則,可以忽略該清單。

 當使用者從 **「檔案** -> **源控制」** 選單中選擇**啟動\<源控制伺服器>** 時,通常會調用此功能。 通過設置註冊表項,始終可以禁用甚至隱藏此**啟動**功能表選項。 有關詳細資訊[,請參閱:安裝原始碼管理外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)。 僅當[Scc 初始化](../extensibility/sccinitialize-function.md)返回`SCC_CAP_RUNSCC`功能位時,才會調用此功能(有關此功能位和其他功能位的詳細資訊,請參閱[功能標誌](../extensibility/capability-flags.md))。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [功能旗標](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
