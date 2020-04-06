---
title: Sccaddfromscc 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701240"
---
# <a name="sccaddfromscc-function"></a>Sccaddfromscc 功能
此功能允許使用者流覽原始程式碼管理系統中已有的檔案,並隨後使這些文件成為當前專案的一部分。 例如,此函數可以在不複製該文件的情況下將公共標頭檔獲取到當前專案中。 檔的`lplpFileNames`傳回數位 包含使用者要新增到 IDE 專案的檔案清單。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpnFiles

[進出]要添加到的文件數的緩衝區。 (這是`NULL`如果指向`lplpFileNames`的 記憶體要釋放。 有關詳細資訊,請參閱備註。

 lplFile 名稱

[進出]指向所有檔名的指標陣列,沒有目錄路徑。 此陣列由原始程式碼管理外掛程式分配和釋放。 如果`lpnFiles` `lplpFileNames` =`NULL`1 和`lplpFileNames`不是 ,則指向的陣列中的第一個名稱包含目標資料夾。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功找到檔並添加到專案中。|
|SCC_I_OPERATIONCANCELED|操作已取消,無效。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|

## <a name="remarks"></a>備註
 IDE 調用此函數。 如果原始程式管理外掛程式支援指定本地目標資料夾,則 IDE`lpnFiles`將傳遞 = 1`lplpFileNames`並將本地資料夾名稱傳遞到中。

 當`SccAddFromScc`對函數的調用返回時,外掛程式已根據需要`lpnFiles`為`lplpFileNames`和分配了檔名陣列的記憶體(請注意,此分配將替換中的`lplpFileNames`指標。 原始程式碼管理外掛程式負責將所有檔案放入使用者的目錄或指定的指定資料夾中。 然後,IDE 將檔添加到IDE專案中。

 最後,IDE 會第二次呼叫此函數,傳`NULL``lpnFiles`入 。 這被解釋為原始程式碼管理外掛程式的特殊訊號,用於釋放為檔名陣組分配的記憶體。`lplpFileNames``.`

 `lplpFileNames`是指針`char ***`。 原始程式碼管理外掛程式放置指向指向檔名的指標陣列的指標,從而以此 API 的標準方式傳遞清單。

> [!NOTE]
> VSSCI API 的初始版本沒有提供指示所添加文件的目標專案的方法。 為了適應這種情況,參數的`lplpFIleNames`語義得到了增強,使其成為輸入/輸出參數,而不是輸出參數。 如果只指定一個檔,即`lpnFiles`由 = 1 指向的值`lplpFileNames`,則的第一個元素包含目標資料夾。 要使用這些新語義,IDE`SccSetOption`將函數呼叫`nOption`, 參數`SCC_OPT_SHARESUBPROJ`設定為 。 如果原始碼管理外掛程式不支援語意,會傳`SCC_E_OPTNOTSUPPORTED`回 。 這樣做將關閉使用從**源控制添加**功能。 如果外掛程式支援 **「從源碼管理新增**」功能`SCC_CAP_ADDFROMSCC`(), 則必須支援新的`SCC_I_SHARESUBPROJOK`語意並傳回 。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
