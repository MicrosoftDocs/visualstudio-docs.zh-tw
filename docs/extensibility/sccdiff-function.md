---
title: SccDiff 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f9f381fbd9c6cb3f4f2128adc3910516be42962
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681656"
---
# <a name="sccdiff-function"></a>SccDiff 函式
此函式會顯示 （或選擇性地只會檢查） 目前的檔案 （位於本機磁碟上） 和最後一個簽入版本之間的差異，即可在來源控制系統。

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
 pvContext

[in]原始檔控制外掛程式的內容結構。

 hWnd

[in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。

 lpFileName

[in]差異要求的檔案名稱。

 fOptions

[in]命令的旗標。 如需詳細資訊，請參閱 < 備註 >。

 pvOptions

[in]原始檔控制外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|工作複本和伺服器版本都相同。|
|SCC_I_FILESDIFFERS|原始檔控制下的版本不同的工作複本。|
|SCC_I_RELOADFILE|必須重新載入檔案或專案。|
|SCC_E_FILENOTCONTROLLED|檔案不是原始檔控制之下。|
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|
|SCC_E_NONSPECIFICERROR|不明確的失敗;無法取得檔案的差異。|
|SCC_E_FILENOTEXIST|找不到本機檔案。|

## <a name="remarks"></a>備註
 此函式有兩種不同的用途。 根據預設，它顯示檔案的變更清單。 原始檔控制外掛程式會自己的視窗中，開啟任何格式，它會選擇，以顯示在磁碟上的使用者的檔案與原始檔控制下的檔案的最新版本之間的差異。

 或者，IDE 可能只需要判斷檔案是否已變更。 比方說，IDE 可能需要判斷它是否安全地簽出檔案，而不通知使用者。 在此情況下，IDE 會傳入`SCC_DIFF_CONTENTS`旗標。 原始檔控制外掛程式必須檢查在磁碟上，逐位元組，針對原始檔控制檔案的檔案，並傳回值，指出兩個檔案是否不同，而不會向使用者顯示任何項目。

 當做效能最佳化，原始檔控制外掛程式可能會使用總和檢查碼或而不是呼叫的逐位元組比較時間戳記為基礎的替代方案`SCC_DIFF_CONTENTS`： 這些形式的比較會很明顯地更快但較不可靠。 並非所有的原始檔控制系統可能會支援這些替代的比較方法，而外掛程式可能切換回內容比較。 所有的原始檔控制外掛程式至少必須支援的內容比較。

> [!NOTE]
>  快速差異旗標互斥。 能夠傳遞任何旗標，但同時傳遞多個無效。 `SCC_DIFF_QUICK_DIFF`這結合了所有的旗標的遮罩可以用來測試，但它應該永遠不會做為參數傳遞。

|`fOption`|意義|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|（可能會用來快速或視覺效果的差異） 的不區分大小寫比較。|
|SCC_DIFF_IGNORESPACE|會忽略泛空白字元 （可能會用來快速或視覺效果的差異）。|
|SCC_DIFF_QD_CONTENTS|以無訊息方式比較檔案，也就是逐位元組。|
|SCC_DIFF_QD_CHECKSUM|以無訊息模式會透過總和檢查碼時支援檔案的比較。 如果不支援，會回復到的內容比較。|
|SCC_DIFF_QD_TIME|以無訊息方式比較透過支援時，其時間戳記的檔案。 如果不支援，會回復到的內容比較。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)