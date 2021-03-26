---
description: 此函式會叫用原始檔控制管理工具。
title: SccRunScc 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e78e58eafebd06d1ce7c710a31ce295b49f26340
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073816"
---
# <a name="sccrunscc-function"></a>SccRunScc 函式
此函式會叫用原始檔控制管理工具。

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
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在陣列中指定的檔案數目 `lpFileNames` 。

 lpFileNames

在所選檔案名的陣列。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功叫用原始檔控制管理工具。|
|SCC_I_OPERATIONCANCELED|作業已取消。|
|SCC_E_INITIALIZEFAILED|無法初始化原始檔控制系統。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。|
|SCC_E_CONNECTIONFAILURE|無法連接到原始檔控制系統。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 這個函式可讓呼叫端透過外部管理工具，存取原始檔控制系統的完整功能範圍。 如果原始檔控制系統沒有使用者介面，則原始檔控制外掛程式可以執行介面來執行必要的管理功能。

 這個函式會使用計數和檔案名陣列來呼叫，以供目前選取的檔案使用。 如果管理工具支援此功能，則可以使用檔案清單來預先設置管理介面中的檔案;否則，可以忽略清單。

 此函式通常會在使用者 **從 [檔案** 原始檔控制] 功能表選取 [ **\<Source Control Server> 啟動**] 時叫用  ->   。 您可以藉由設定登錄專案，一律停用或甚至隱藏這個 **啟動** 功能表選項。 如需詳細資訊，請參閱 [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md) 。 只有當 [SccInitialize](../extensibility/sccinitialize-function.md) 傳回功能位時，才會呼叫此函式 `SCC_CAP_RUNSCC` (請參閱 [功能旗標](../extensibility/capability-flags.md) ，以取得此功能和其他功能位) 的詳細資料。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [功能旗標](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
