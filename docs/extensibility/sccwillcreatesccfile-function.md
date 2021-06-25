---
description: 此函式會判斷原始檔控制外掛程式是否支援建立 MSSCCPRJ.SCC。每個指定檔案的 SCC 檔。
title: SccWillCreateSccFile 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f9e6df29b9f44d852c7c84488a3febf590fcc0e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900443"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函式
此函式會判斷原始檔控制外掛程式是否支援建立 MSSCCPRJ.SCC。每個指定檔案的 SCC 檔。

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

在原始檔控制外掛程式內容指標。

 nFiles

在陣列中包含的檔案名以及 `lpFileNames` 陣列的長度 `pbSccFiles` 。

 lpFileNames

在要檢查 (陣列的完整檔案名陣列必須由呼叫端) 進行配置。

 pbSccFiles

[in，out]要在其中儲存結果的陣列。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_INVALIDFILEPATH|陣列中的其中一個路徑無效。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 這個函式會使用檔案清單來呼叫，以判斷原始檔控制外掛程式是否在 MSSCCPRJ.SCC 中提供支援。每個指定檔案的 SCC 檔 (如需 MSSCCPRJ.SCC 的詳細資訊，請。SCC 檔案，請參閱 [mssccprj.scc。SCC](../extensibility/mssccprj-scc-file.md) 檔案) 。 原始檔控制外掛程式可以宣告它們是否有建立 MSSCCPRJ.SCC 的能力。在初始化期間宣告的 SCC 檔 `SCC_CAP_SCCFILE` 。 外掛程式 `TRUE` `FALSE` 會傳回陣列中的或每個檔案 `pbSccFiles` ，以指出指定的檔案有何 mssccprj.scc。SCC 支援。 如果外掛程式從函式傳回成功的程式碼，則會接受傳回陣列中的值。 失敗時，會忽略陣列。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)
