---
title: IApplicationDebuggerUI：： BringDocumentCoNtextToTop |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577816"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
將包含給定檔內容的視窗帶入偵錯工具使用者介面中的頂端，並將視窗滾動至內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pddc`  
 在要在偵錯工具使用者介面中帶入頂端的檔內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|@No__t_0 所指定的內容是未知的。|  
  
## <a name="remarks"></a>備註  
 這個方法會將包含給定檔內容的視窗帶入偵錯工具使用者介面中的頂端，並將視窗滾動至內容。  
  
## <a name="see-also"></a>請參閱  
 [IApplicationDebuggerUI 介面](../../winscript/reference/iapplicationdebuggerui-interface.md)