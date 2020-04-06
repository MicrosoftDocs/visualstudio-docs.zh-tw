---
title: Sccwill 創建sccfile功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700203"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 函式
此功能確定原始程式碼管理外掛程式是否支援 MSSCCPRJ 的創建。每個給定檔的 SCC 檔。

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

[在]源代碼管理外掛程式上下文指標。

 n 檔案

[在]`lpFileNames`陣列包含的檔名數以及`pbSccFiles`數位的長度。

 lpFile 名稱

[在]要檢查的完全限定檔名陣列(陣列必須由調用方分配)。

 pbScc 檔

[進出]用於存儲結果的陣列。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_INVALIDFILEPATH|陣列中的一個路徑無效。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 使用檔案清單調用此功能,以確定原始程式碼管理外掛程式是否在 MSSCCPRJ 中提供支援。每個給定檔的 SCC 檔(有關 MSSCCPRJ 的詳細資訊。SCC 檔,請參閱[MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)。 原始程式可以聲明它們是否具有創建 MSSCCPRJ 的功能。通過在初始化期間聲明`SCC_CAP_SCCFILE`SCC 檔。 外掛程式`TRUE`傳`FALSE`回 或`pbSccFiles`數位中的 每個檔,以指示哪些給定檔具有 MSSCCPRJ。SCC 支援。 如果外掛程式返回函數中的成功代碼,則將尊重返回陣列中的值。 發生故障時,將忽略陣列。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)
