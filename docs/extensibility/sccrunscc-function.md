---
title: SccRunScc 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720545"
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

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 n

在@No__t_0 陣列中指定的檔案數目。

 lpFileNames

在選取的檔案名陣列。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功叫用原始檔控制管理工具。|
|SCC_I_OPERATIONCANCELED|作業已取消。|
|SCC_E_INITIALIZEFAILED|無法初始化原始檔控制系統。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。|
|SCC_E_CONNECTIONFAILURE|無法連接到原始檔控制系統。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 此函式可讓呼叫者透過外部管理工具，存取原始檔控制系統的完整功能範圍。 如果原始檔控制系統沒有使用者介面，原始檔控制外掛程式就可以執行介面來執行必要的系統管理功能。

 這個函式會使用計數和檔案名陣列來呼叫，以用於目前選取的檔案。 如果管理工具支援此功能，則可以使用檔案清單來預先填入系統管理介面中的檔案;否則，可以忽略此清單。

 當使用者**從 [檔案**]  ->  [原始檔**控制**] 功能表中選取 [**啟動 \<Source 控制伺服器 >** ] 時，通常會叫用此函式。 藉由設定登錄專案，可以一律停用或甚至隱藏此**啟動**功能表選項。 如需詳細資訊，請參閱[如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)。 只有在[SccInitialize](../extensibility/sccinitialize-function.md)傳回 `SCC_CAP_RUNSCC` 的功能位時，才會呼叫這個函式（如需此和其他功能位的詳細資料，請參閱[功能旗標](../extensibility/capability-flags.md)）。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [功能旗標](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)