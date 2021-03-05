---
description: 此函式會初始化原始檔控制外掛程式，並提供整合式開發環境 (IDE) 的功能和限制。
title: SccInitialize 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 986e3624b1716c782102f0f214283a7fa7020a08
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220582"
---
# <a name="sccinitialize-function"></a>SccInitialize 函式
此函式會初始化原始檔控制外掛程式，並提供整合式開發環境 (IDE) 的功能和限制。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>參數
 `ppvContext`

在原始檔控制外掛程式可以在此放置其內容結構的指標。

 `hWnd`

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 `lpCallerName`

在呼叫原始檔控制外掛程式的程式名稱。

 `lpSccName`

[in，out]原始檔控制外掛程式放置它自己的名稱 (不會超過) 的緩衝區 `SCC_NAME_LEN` 。

 `lpSccCaps`

擴展傳回原始檔控制外掛程式的功能旗標。

 `lpAuxPathLabel`

[in，out]原始檔控制外掛程式放置字串的緩衝區，此字串描述 `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md) 和 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) 所傳回的參數 (不會超過 `SCC_AUXLABEL_LEN`) 。

 `pnCheckoutCommentLen`

擴展傳回簽出批註允許的最大長度。

 `pnCommentLen`

擴展傳回其他批註允許的最大長度。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|原始檔控制初始化成功。|
|SCC_E_INITIALIZEFAILED|無法初始化系統。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行指定的操作。|
|SCC_E_NONSPECFICERROR|模糊失敗;原始檔控制系統未初始化。|

## <a name="remarks"></a>備註
 IDE 第一次載入原始檔控制外掛程式時，會呼叫此函數。 它可讓 IDE 將某些資訊（例如呼叫端名稱）傳遞給外掛程式。 IDE 也會取得某些資訊，例如批註的最大容許長度和外掛程式的功能。

 指向 `ppvContext` `NULL` 指標的。 原始檔控制外掛程式可以為它自己的用途配置結構，並將該結構的指標儲存在中 `ppvContext` 。 IDE 會將此指標傳遞至每個其他 VSSCI API 函式，讓外掛程式可以使用內容資訊，而不需要利用全域儲存體，並支援多個外掛程式實例。 呼叫 [SccUninitialize](../extensibility/sccuninitialize-function.md) 時，應該將此結構解除配置。

 `lpCallerName`和 `lpSccName` 參數可讓 IDE 和原始檔控制外掛程式交換名稱。 這些名稱只是用來區別多個實例，或可能實際出現在功能表或對話方塊中。

 `lpAuxPathLabel`參數是用來做為批註的字串，用來識別儲存在方案檔中的輔助專案路徑，並傳遞至[SccOpenProject](../extensibility/sccopenproject-function.md)呼叫中的原始檔控制外掛程式。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 使用 "SourceSafe Project：" 字串。其他原始檔控制外掛程式應避免使用這個特定的字串。

 `lpSccCaps`參數會提供原始檔控制外掛程式儲存位旗標的位置，指出外掛程式的功能。  (如需功能位旗標的完整清單，請參閱 [功能旗標](../extensibility/capability-flags.md)) 。 比方說，如果外掛程式計畫將結果寫入呼叫端提供的回呼函式，則外掛程式會設定 SCC_CAP_TEXTOUT 的功能位。 這會通知 IDE 建立版本控制結果的視窗。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [功能旗標](../extensibility/capability-flags.md)
