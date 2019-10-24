---
title: SccWillCreateSccFile 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720110"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函式
此函式會判斷原始檔控制外掛程式是否支援建立 MSSCCPRJ.SCC。適用于每個指定檔案的 SCC 檔案。

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
 pCoNtext

在原始檔控制外掛程式內容指標。

 n

在@No__t_0 陣列中包含的檔案名數目，以及 `pbSccFiles` 陣列的長度。

 lpFileNames

在要檢查的完整檔案名陣列（陣列必須由呼叫者配置）。

 pbSccFiles

[in、out]要在其中儲存結果的陣列。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_INVALIDFILEPATH|陣列中的其中一個路徑無效。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 這個函式會使用檔案清單來呼叫，以判斷原始檔控制外掛程式是否在 MSSCCPRJ.SCC 中提供支援。適用于每個指定檔案的 SCC 檔案（如需 MSSCCPRJ.SCC 的詳細資訊，請查看。SCC 檔案，請參閱[mssccprj.scc。SCC](../extensibility/mssccprj-scc-file.md)檔案）。 原始檔控制外掛程式可以宣告是否有建立 MSSCCPRJ.SCC 的功能。在初始化期間宣告 `SCC_CAP_SCCFILE` 的 SCC 檔案。 外掛程式會針對 `pbSccFiles` 陣列中的每個檔案傳回 `TRUE` 或 `FALSE`，以指出給定檔案的 MSSCCPRJ.SCC。SCC 支援。 如果外掛程式從函式傳回成功的程式碼，則會接受傳回陣列中的值。 失敗時，會忽略陣列。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)