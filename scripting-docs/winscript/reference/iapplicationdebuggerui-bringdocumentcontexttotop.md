---
title: IApplicationDebuggerUI::BringDocumentContextToTop |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 890cc1b6c38f44c4140274dcaa19deff1fd276e2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095507"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
會包含偵錯工具使用者介面中的第一個指定的文件內容的視窗，以及捲動視窗至內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddc`  
 [in]在偵錯工具使用者介面中將顯示在上面的文件內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|所指定的內容`pddc`未知。|  
  
## <a name="remarks"></a>備註  
 這個方法會包含偵錯工具使用者介面中的第一個指定的文件內容的視窗，並捲動視窗至內容。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)