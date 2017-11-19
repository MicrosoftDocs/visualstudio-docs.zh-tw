---
title: "IApplicationDebuggerUI::BringDocumentContextToTop |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
包含偵錯工具使用者介面中最上層的給定文件內容的視窗，且捲動視窗至內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddc`  
 [in]若要將偵錯工具使用者介面中帶入頂端的文件內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|所指定的內容`pddc`不明。|  
  
## <a name="remarks"></a>備註  
 這個方法會將包含偵錯工具使用者介面中最上層的給定文件內容的視窗，並捲動視窗至內容。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)