---
title: SccWillCreateSccFile 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fa85c8a96f17508d2e2e53a8d14444dd857dad0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800281"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函式
此函式會判斷原始檔控制外掛程式是否支援 MSSCCPRJ 建立。SCC 檔案，每個指定的檔案。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>參數
 pContext

[in]原始檔控制外掛程式的內容指標。

 nFiles

[in]檔案名稱中包含的數字`lpFileNames`陣列的長度以及`pbSccFiles`陣列。

 lpFileNames

[in]若要檢查的完整的檔案名稱的陣列 （必須由呼叫端配置陣列）。

 pbSccFiles

[in、 out]用來儲存結果的陣列。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_INVALIDFILEPATH|其中一個陣列中的路徑無效。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 會呼叫此函數，來判斷是否原始檔控制外掛程式提供 MSSCCPRJ 中支援的檔案清單中。SCC 檔案，每個指定的檔案 （如需有關 MSSCCPRJ 的詳細資訊。SCC 檔案，請參閱[MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md))。 原始檔控制外掛程式可以宣告它們是否具有建立 MSSCCPRJ 的功能。SCC 檔案，藉由宣告`SCC_CAP_SCCFILE`在初始化期間。 此外掛程式會傳回`TRUE`或是`FALSE`每個檔案中`pbSccFiles`陣列，表示其中一個指定的檔案有 MSSCCPRJ。SCC 的支援。 如果外掛程式會傳回成功的程式碼從函式，則會遵守傳回陣列中的值。 在失敗時，陣列會被忽略。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)