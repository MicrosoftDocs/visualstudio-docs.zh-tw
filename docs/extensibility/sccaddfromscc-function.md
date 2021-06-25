---
description: 這個函式可讓使用者流覽已在原始檔控制系統中的檔案，然後再將這些檔案設為目前專案的一部分。
title: SccAddFromScc 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904872"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 函式
這個函式可讓使用者流覽已在原始檔控制系統中的檔案，然後再將這些檔案設為目前專案的一部分。 例如，此函式可以在不復制檔案的情況下，取得目前專案的通用標頭檔。 傳回的檔案陣列， `lplpFileNames` 包含使用者想要新增至 IDE 專案的檔案清單。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpnFiles

[in，out]要加入之檔案數目的緩衝區。  (這是 `NULL` 為了釋放所指向的記憶體 `lplpFileNames` 。 如需詳細資訊，請參閱備註。 ) 

 lplpFileNames

[in，out]所有檔案名的指標陣列，而不包含目錄路徑。 這個陣列是由原始檔控制外掛程式配置和釋放。 如果 `lpnFiles` = 1 且不 `lplpFileNames` 是 `NULL` ，則由所指向之陣列中的第一個名稱 `lplpFileNames` 包含目的資料夾。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|檔案已成功找出並新增至專案。|
|SCC_I_OPERATIONCANCELED|作業已取消，沒有任何作用。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|

## <a name="remarks"></a>備註
 IDE 會呼叫這個函數。 如果原始檔控制外掛程式支援指定本機目的資料夾，則 IDE 會傳遞 `lpnFiles` = 1，並將本機資料夾名稱傳遞至 `lplpFileNames` 。

 當函式的呼叫傳回時 `SccAddFromScc` ，外掛程式已將值指派給 `lpnFiles` 和 `lplpFileNames` ，視需要設定檔案名稱陣列的記憶體 (請注意，此配置會取代) 中的指標 `lplpFileNames` 。 原始檔控制外掛程式負責將所有檔案放入使用者的目錄或指定的指定資料夾中。 IDE 接著會將檔案新增至 IDE 專案。

 最後，IDE 會第二次呼叫此函式，並 `NULL` 傳入 `lpnFiles` 。 這會被原始檔控制外掛程式解釋為特殊信號，以釋放配置給中的檔案名陣列的記憶體。 `lplpFileNames``.`

 `lplpFileNames` 是 `char ***` 指標。 原始檔控制外掛程式會放置指向檔案名之指標陣列的指標，進而以標準方式傳遞此 API 的清單。

> [!NOTE]
> VSSCI API 的初始版本並未提供方法來指出新增檔案的目標專案。 為了因應這種情況， `lplpFIleNames` 已增強參數的語法，使其成為 in/out 參數，而非 output 參數。 如果只指定單一檔案，也就是由 = 1 指向的值， `lpnFiles` 則的第一個元素會 `lplpFileNames` 包含目的檔案夾。 若要使用這些新的語義，IDE 會呼叫 `SccSetOption` 函數，並將 `nOption` 參數設定為 `SCC_OPT_SHARESUBPROJ` 。 如果原始檔控制外掛程式不支援此語義，則會傳回 `SCC_E_OPTNOTSUPPORTED` 。 這麼做會停用 [ **從原始檔控制加入** ] 功能。 如果外掛程式支援 [ **從原始檔控制加入** ] 功能 (`SCC_CAP_ADDFROMSCC`) ，則必須支援新的語義並傳回 `SCC_I_SHARESUBPROJOK` 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
