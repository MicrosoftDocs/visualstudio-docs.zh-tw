---
title: SccInitialize 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721176"
---
# <a name="sccinitialize-function"></a>SccInitialize 函式
此函式會初始化原始檔控制外掛程式，並提供整合式開發環境（IDE）的功能和限制。

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

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 `lpCallerName`

在呼叫原始檔控制外掛程式的程式名稱。

 `lpSccName`

[in、out]原始檔控制外掛程式用來放置其本身名稱的緩衝區（不會超過 `SCC_NAME_LEN`）。

 `lpSccCaps`

脫銷傳回原始檔控制外掛程式的功能旗標。

 `lpAuxPathLabel`

[in、out]原始檔控制外掛程式所放置的字串，會描述[SccOpenProject](../extensibility/sccopenproject-function.md)和[SccGetProjPath](../extensibility/sccgetprojpath-function.md)所傳回的 `lpAuxProjPath` 參數（不會超過 `SCC_AUXLABEL_LEN`）。

 `pnCheckoutCommentLen`

脫銷傳回簽出批註的最大允許長度。

 `pnCommentLen`

脫銷傳回其他批註的最大容許長度。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|原始檔控制初始化成功。|
|SCC_E_INITIALIZEFAILED|無法初始化系統。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行指定的作業。|
|SCC_E_NONSPECFICERROR|模糊失敗;原始檔控制系統尚未初始化。|

## <a name="remarks"></a>備註
 IDE 第一次載入原始檔控制外掛程式時，會呼叫這個函式。 它可讓 IDE 將特定資訊（例如呼叫者名稱）傳遞給外掛程式。 IDE 也會傳回某些資訊，例如最大可允許的批註長度和外掛程式的功能。

 @No__t_0 指向 `NULL` 指標。 原始檔控制外掛程式可以配置結構供自己使用，並在 `ppvContext` 中儲存該結構的指標。 IDE 會將這個指標傳遞給每個其他 VSSCI API 函式，讓外掛程式可以使用內容資訊，而不需要經過全域儲存並支援外掛程式的多個實例。 呼叫[SccUninitialize](../extensibility/sccuninitialize-function.md)時，應該解除配置此結構。

 @No__t_0 和 `lpSccName` 參數可讓 IDE 和原始檔控制外掛程式交換名稱。 這些名稱只能用來區別多個實例，也可以實際出現在功能表或對話方塊中。

 @No__t_0 參數是用來做為批註的字串，用來識別儲存在方案檔中的輔助專案路徑，並在呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)時傳遞至原始檔控制外掛程式。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 使用字串 "SourceSafe Project：";其他原始檔控制外掛程式應該避免使用這個特定的字串。

 @No__t_0 參數可讓原始檔控制外掛程式儲存位旗標，以指出外掛程式的功能。 （如需功能位旗標的完整清單，請參閱[功能旗標](../extensibility/capability-flags.md)）。 例如，如果外掛程式計畫將結果寫入呼叫端提供的回呼函式中，則外掛程式會設定功能位 SCC_CAP_TEXTOUT。 這會指示 IDE 建立版本控制結果的視窗。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [功能旗標](../extensibility/capability-flags.md)