---
title: SccEnumChangedFiles 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9bc2738e9a4d7cac0d57b9c613b7070f60baff
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711550"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 函式
指定本機檔案的清單，此函式，判斷哪些檔案是從原始程式碼控制資料庫中對應的版本不同。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>參數
 pContext

[in]原始檔控制外掛程式的內容指標。

 hWnd

[in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。

 cFiles

[in]中指定的檔案名稱數目`lpFileNames`陣列。 也會指定大小`plIsFileDifferent`陣列。

 lpFileNames

[in]若要檢查的本機檔案名稱的陣列。

 plIsFileDifferent

[in、 out]值，表示每個檔案的不同狀態的陣列 (陣列至少必須有`cFiles`項目)。 非零值的方法，是不同的檔案。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|作業已順利完成。|
|SCC_UNSPECIFIEDERROR|一般錯誤。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)