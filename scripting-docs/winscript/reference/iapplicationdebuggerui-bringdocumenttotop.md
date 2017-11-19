---
title: "IApplicationDebuggerUI::BringDocumentToTop |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57b76f44eeeaad1946d40435c770b0687b82fd17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
將包含偵錯工具中的第一個指定的偵錯文件視窗顯示使用者介面。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddt`  
 [in]偵錯的偵錯工具使用者介面中將顯示在上面的文件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|不知道文件。|  
  
## <a name="remarks"></a>備註  
 這個方法將包含偵錯工具中的第一個指定的偵錯文件視窗顯示使用者介面。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)