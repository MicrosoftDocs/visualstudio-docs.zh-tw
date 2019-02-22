---
title: 'Ijsdebugframe:: Getdocumentpositionwithname 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d6333f9c52c3ab4e0cd01c34f5e5228721aa55b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093830"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName 方法
傳回此堆疊框架，在使用者層級文件中的目前位置。  
  
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
 [out]為靜態的指令碼、 文件的 URL。 針對動態指令碼，會傳回包含指令碼 （例如，評估程式碼，函式程式碼等） 的類型名稱。  
  
 `pLine`  
 [out] 文件中的以 1 起始的行位置。  
  
 `pColumn`  
 [out] 文件中的以 1 起始的行位置。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** jscript9diag.h  
  
## <a name="see-also"></a>另請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)