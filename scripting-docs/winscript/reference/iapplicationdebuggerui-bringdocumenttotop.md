---
title: IApplicationDebuggerUI::BringDocumentToTop |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c77c87011c539e02f92aa2aedfdcd7659466d37
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096248"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
使用者介面將包含偵錯工具中的第一個指定的偵錯文件的視窗。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddt`  
 [in]偵錯的偵錯工具使用者介面中將顯示在上面的文件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|不知道文件。|  
  
## <a name="remarks"></a>備註  
 這個方法將包含指定的偵錯文件來偵錯工具中的第一個視窗顯示使用者介面。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)