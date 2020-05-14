---
title: SccEnum更改檔案功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700910"
---
# <a name="sccenumchangedfiles-function"></a>SccEnum 更改檔案功能
給定本地檔案的清單,此函數確定哪些檔不同於原始程式碼管理資料庫中的相應版本。

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

[在]源代碼管理外掛程式上下文指標。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 cFiles

[在]`lpFileNames`陣列中指定的檔名數。 您可以指定陣列的`plIsFileDifferent`大小 。

 lpFile 名稱

[在]要檢查的本地檔名陣列。

 PlIsFile 不同

[進出]指示每個文件差異狀態的值陣列(陣列必須至少有`cFiles`項目)。 非零表示檔不同。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|作業順利完成。|
|SCC_UNSPECIFIEDERROR|一般錯誤。|

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
