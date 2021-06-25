---
description: 此函式會顯示 (，或選擇性地檢查) 本機) 磁片上的目前檔案 (與原始檔控制系統中的最後一個簽入版本之間的差異。
title: SccDiff 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904652"
---
# <a name="sccdiff-function"></a>SccDiff 函式
此函式會顯示 (，或選擇性地檢查) 本機) 磁片上的目前檔案 (與原始檔控制系統中的最後一個簽入版本之間的差異。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpFileName

在要求差異的檔案名。

 fOptions

在命令旗標。 如需詳細資訊，請參閱備註。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|工作複本和伺服器版本完全相同。|
|SCC_I_FILESDIFFERS|工作複本與原始檔控制下的版本不同。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制之下。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR|模糊失敗;未取得檔案差異。|
|SCC_E_FILENOTEXIST|找不到本機檔案。|

## <a name="remarks"></a>備註
 這個函式有兩個不同的用途。 依預設，它會顯示檔案的變更清單。 原始檔控制外掛程式會以它選擇的任何格式開啟自己的視窗，以顯示使用者在磁片上的檔案與原始檔控制下的最新版本之間的差異。

 或者，IDE 可能只需要判斷檔案是否已變更。 例如，IDE 可能需要判斷是否可以安全地簽出檔案，而不通知使用者。 在此情況下，IDE 會傳入 `SCC_DIFF_CONTENTS` 旗標。 原始檔控制外掛程式必須針對原始檔控制的檔案，檢查磁片上的檔案（以位元組為單位），並傳回值，指出兩個檔案是否不同，而不會向使用者顯示任何資訊。

 基於效能優化，原始檔控制外掛程式可能會根據總和檢查碼或時間戳記使用替代方法，而不是針對所呼叫的逐位元組比較 `SCC_DIFF_CONTENTS` ：這些形式的比較明顯較快，但較不可靠。 並非所有的原始檔控制系統都可支援這些替代的比較方法，而且外掛程式可能必須切換回內容比較。 所有原始檔控制外掛程式至少都必須支援內容比較。

> [!NOTE]
> 快速差異旗標彼此互斥。 不傳遞旗標是有效的，但不能同時傳遞多個旗標是不正確。 `SCC_DIFF_QUICK_DIFF`這是結合所有旗標的遮罩，可用來進行測試，但是絕不能以參數的形式傳遞。

|`fOption`|意義|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|不區分大小寫的比較 (可用於快速或視覺差異) 。|
|SCC_DIFF_IGNORESPACE|忽略空白字元 (可用於快速或視覺差異) 。|
|SCC_DIFF_QD_CONTENTS|以無訊息方式比較檔案（位元組）。|
|SCC_DIFF_QD_CHECKSUM|以無訊息方式透過總和檢查碼比較檔案（如果支援的話）。 如果不支援，則會回復到內容的比較。|
|SCC_DIFF_QD_TIME|在支援時，以無訊息方式比較檔案的時間戳記。 如果不支援，則會回復到內容的比較。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
