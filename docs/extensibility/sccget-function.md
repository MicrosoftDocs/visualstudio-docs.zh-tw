---
title: SccGet 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50281ffdd233debd3c10672868e9debd4b1f395f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965209"
---
# <a name="sccget-function"></a>SccGet 函式
此函式會取得一或多個檔案的複本，以供您進行編輯，但無法進行編輯。 在大部分的系統中，會將檔案標記為唯讀。

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
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在陣列中指定的檔案數目 `lpFileNames` 。

 lpFileNames

在要抓取之檔案的完整限定名稱陣列。

 fOptions

在命令旗標 (`SCC_GET_ALL` ， `SCC_GET_RECURSIVE`) 。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功的 get 作業。|
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制之下。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這種操作。|
|SCC_E_FILEISCHECKEDOUT|無法取得使用者目前已簽出的檔案。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NOSPECIFIEDVERSION|指定了不正確版本或日期/時間。|
|SCC_E_NONSPECIFICERROR|模糊失敗;檔案未同步處理。|
|SCC_I_OPERATIONCANCELED|作業在完成前取消。|
|SCC_E_NOTAUTHORIZED|未授權使用者執行此作業。|

## <a name="remarks"></a>備註
 呼叫此函式時，會使用計數和要抓取之檔案的名稱陣列。 如果 IDE 傳遞旗標 `SCC_GET_ALL` ，這表示中的專案 `lpFileNames` 不是檔案，而是目錄，而且在指定目錄中的所有檔案都會被抓取。

 `SCC_GET_ALL`旗標可以與旗標結合， `SCC_GET_RECURSIVE` 以取得指定目錄和所有子目錄中的所有檔案。

> [!NOTE]
> `SCC_GET_RECURSIVE` 永遠不會在沒有的情況下傳遞 `SCC_GET_ALL` 。 此外，請注意，如果目錄 *C:\A* 和 *C:\A\B* 都是以遞迴 get 傳遞，則 *C:\A\B* 及其所有子目錄實際上會被取出兩次。 這是 IDE 的責任（而不是原始檔控制外掛程式），以確保這些重複專案（例如這類）會保留在陣列外。

 最後，即使原始檔控制外掛程式在初始化時指定 `SCC_CAP_GET_NOUI` 旗標，表示它沒有 Get 命令的使用者介面，IDE 仍會呼叫此函式來取出檔案。 旗標只是表示 IDE 不會顯示 Get 功能表項目，而且不應該提供任何 UI 給外掛程式。

## <a name="rename-files-and-sccget"></a>重新命名檔案和 SccGet
 狀況：使用者簽出檔案，例如 *a.txt*，並加以修改。 在 *a.txt* 可以簽入之前，第二位使用者將 *a.txt* 重新命名為原始檔控制資料庫中的 *b.txt* 、簽出 *b.txt*、對檔案進行一些修改，並在中檢查檔案。 第一位使用者想要進行第二位使用者所做的變更，讓第一位使用者將 *a.txt* 檔案的本機版本重新命名為 *b.txt* ，然後在檔案上執行 get。 不過，追蹤版本號碼的本機快取仍會認為 *a.txt* 的第一個版本會儲存在本機，因此原始檔控制無法解決這些差異。

 有兩種方式可以解決這種情況，亦即原始檔控制版本的本機快取與原始檔控制資料庫不同步：

1. 不允許在目前簽出的原始檔控制資料庫中重新命名檔案。

2. 等同于 "delete old"，後面接著「新增」。 下列演算法是完成這項操作的一種方法。

    1. 呼叫 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 函數，以瞭解如何將 *a.txt* 重新命名為原始檔控制資料庫中 *b.txt* 的。

    2. 將本機 *a.txt* 重新命名為 *b.txt*。

    3. `SccGet`針對 *a.txt* 和 *b.txt* 呼叫函數。

    4. 由於 *a.txt* 不存在於原始檔控制資料庫中，因此會清除缺少的 *a.txt* 版本資訊的本機版本快取。

    5. 要簽出的 *b.txt* 檔案會與本機 *b.txt* 檔案的內容合併。

    6. 現在可以簽入更新的 *b.txt* 檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [特定命令所使用的位旗標](../extensibility/bitflags-used-by-specific-commands.md)
