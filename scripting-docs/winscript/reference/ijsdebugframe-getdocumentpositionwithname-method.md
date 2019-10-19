---
title: IJsDebugFrame：： GetDocumentPositionWithName 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575115"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName 方法
傳回此堆疊框架在使用者層級檔中的目前位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDocumentName`  
 脫銷若為靜態腳本，則為檔的 URL。 若為動態腳本，則會傳回包含腳本類型的名稱（例如，評估程式碼、函式程式碼等）。  
  
 `pLine`  
 [out] 檔中以1為基礎的行位置。  
  
 `pColumn`  
 [out] 檔中以1為基礎的行位置。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag。h  
  
## <a name="see-also"></a>請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)