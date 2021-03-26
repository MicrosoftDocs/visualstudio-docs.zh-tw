---
description: 此函式會顯示用戶端磁片上目前本機目錄與原始檔控制下對應專案之間的差異。
title: SccDirDiff 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 974d0aa22ff3940472be34b691a61632dc742223
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073972"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 函式
此函式會顯示用戶端磁片上目前本機目錄與原始檔控制下對應專案之間的差異。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpDirName

在要顯示其視覺效果差異之本機目錄的完整路徑。

 dwFlags

在命令旗標 (查看備註區段) 。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|磁片上的目錄與原始程式碼控制中的專案相同。|
|SCC_I_FILESDIFFER|磁片上的目錄與原始程式碼控制中的專案不同。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|
|SCC_E_FILENOTCONTROLLED|此目錄不在原始程式碼控制之下。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|模糊失敗。|
|SCC_E_FILENOTEXIST|找不到本機目錄。|

## <a name="remarks"></a>備註
 這個函式是用來指示原始檔控制外掛程式向使用者顯示指定目錄的變更清單。 外掛程式會以其選擇的格式開啟自己的視窗，以顯示使用者在磁片上的目錄與版本控制下的對應專案之間的差異。

 如果外掛程式支援目錄的比較，則即使不支援「快速差異」選項，它也必須支援目錄的目錄比較。

|`dwFlags`|解讀|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|不區分大小寫的比較 (可用於快速差異或 visual) 。|
|SCC_DIFF_IGNORESPACE|忽略空白字元 (可用於快速差異或 visual) 。|
|SCC_DIFF_QD_CONTENTS|如果原始檔控制外掛程式支援，則以無訊息方式比較目錄、位元組和位元組。|
|SCC_DIFF_QD_CHECKSUM|如果外掛程式支援，請透過總和檢查碼以無訊息方式比較目錄，或者，如果不支援，則會回復為 SCC_DIFF_QD_CONTENTS。|
|SCC_DIFF_QD_TIME|如果外掛程式支援，請以無訊息方式透過其時間戳記來比較目錄，或者，如果不支援，則會回到 SCC_DIFF_QD_CHECKSUM 或 SCC_DIFF_QD_CONTENTS。|

> [!NOTE]
> 此函數會使用與 [SccDiff](../extensibility/sccdiff-function.md)相同的命令旗標。 不過，原始檔控制外掛程式可能會選擇不支援目錄的「快速差異」作業。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
