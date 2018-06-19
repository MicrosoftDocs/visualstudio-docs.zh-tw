---
title: SccEnumChangedFiles 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 762bda21f8480224347bd0c8c202c282298e07cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137127"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 函式
指定本機檔案的清單，此函式，判斷哪些檔案會從原始程式碼控制資料庫中對應的版本不同。  
  
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
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容指標。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 cFiles  
 [in]檔案名稱中指定的數目`lpFileNames`陣列。 也會指定的大小`plIsFileDifferent`陣列。  
  
 lpFileNames  
 [in]若要檢查的本機檔案名稱的陣列。  
  
 plIsFileDifferent  
 [in、 out]值，指出每個檔案的不同狀態的陣列 (陣列至少必須有`cFiles`項目)。 檔案不相同則為非零的方式。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|作業已順利完成。|  
|SCC_UNSPECIFIEDERROR|發生一般錯誤。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)