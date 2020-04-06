---
title: SccGet 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700894"
---
# <a name="sccget-function"></a>SccGet 函數
此函數檢索一個或多個檔的副本,用於查看和編譯,但不用於編輯。 在大多數系統中,文件標記為唯讀。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式的上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]`lpFileNames`陣列中指定的檔案數。

 lpFile 名稱

[在]要檢索的檔完全限定名稱的陣列。

 fOptions

[在]命令標誌`SCC_GET_ALL`(。 `SCC_GET_RECURSIVE`

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功獲得操作。|
|SCC_E_FILENOTCONTROLLED|該檔不受原始程式碼管理。|
|SCC_E_OPNOTSUPPORTED|原始程式碼管理系統不支援此操作。|
|SCC_E_FILEISCHECKEDOUT|無法取得使用者目前已簽出的檔。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NOSPECIFIEDVERSION|指定無效的版本或日期/時間。|
|SCC_E_NONSPECIFICERROR|非特異性故障;檔未同步。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|
|SCC_E_NOTAUTHORIZED|未授權使用者執行此作業。|

## <a name="remarks"></a>備註
 此函數使用要檢索的檔的計數和名稱陣列進行調用。 如果 IDE`SCC_GET_ALL`傳遞標誌 ,`lpFileNames`則意味著 中的項不是檔,而是目錄,並且要檢索給定目錄中源控制下的所有檔。

 該`SCC_GET_ALL`標誌可以與標誌組合`SCC_GET_RECURSIVE`, 以檢索給定目錄中的所有檔和所有子目錄。

> [!NOTE]
> `SCC_GET_RECURSIVE`不應通過沒有`SCC_GET_ALL`。 此外,請注意,如果目錄*C:\A*和*C:\A\B*都傳遞遞歸獲取,則*C:\A\B*及其所有子目錄實際上將被檢索兩次。 IDE 有責任(而不是原始程式碼管理外掛程式)確保此類重複項遠離陣列。

 最後,即使原始程式碼管理外掛程式在初始化`SCC_CAP_GET_NOUI`時指定了標誌,表示它沒有 Get 命令的使用者介面,IDE 仍可能呼叫此功能來檢索檔。 該標誌僅表示 IDE 不顯示 Get 功能表項,並且外掛程式不應提供任何 UI。

## <a name="rename-files-and-sccget"></a>重新命名檔案與 SccGet
 情況:使用者簽出檔,例如*a.txt*,並修改該檔。 在可以簽入*a.txt*之前,第二個使用者將在原始程式碼管理資料庫中將*a.txt*重新命名為*b.txt,* 簽出*b.txt,* 對檔案進行一些修改,然後簽入該檔。 第一個使用者希望第二個使用者所做的更改,以便第一個使用者將其本地版本的*a.txt*檔重新命名為*b.txt,* 並執行檔獲取。 但是,跟蹤版本號的本地緩存仍然認為*a.txt*的第一個版本存儲在本地,因此原始程式碼管理無法解決這些差異。

 有兩種方法可以解決此問題,即原始碼管理版本的本地快取與原始碼管理資料庫不同步:

1. 不要重新命名目前簽出的原始碼管理資料庫中的檔案。

2. 執行等效的"刪除舊"後跟"添加新"。 以下演演演算法是實現此目的的一種方法。

    1. 呼叫[SccQuery 更改](../extensibility/sccquerychanges-function.md)函數以瞭解在原始程式碼管理資料庫中將*a.txt*重新命名為*b.txt。*

    2. 將本地*端 a.txt*重新命名為*b.txt*。

    3. 調用`SccGet`*a.txt*和*b.txt 的*函數。

    4. 由於原始碼管理資料庫中不存在*a.txt,* 因此將清除缺少*的 a.txt*版本資訊的本地版本緩存。

    5. 要簽出的*b.txt*檔將與本地*b.txt*檔的內容合併。

    6. 現在可以簽入更新的*b.txt*檔。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [特定指令使用的位元號](../extensibility/bitflags-used-by-specific-commands.md)
