---
title: IDebugDocumentHelper：:D efineScriptBlock |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576983"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
向 helper 表示特定範圍的字元是由指定的腳本引擎所處理的腳本區塊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulCharOffset`  
 在腳本區塊開頭的位置。  
  
 `cChars`  
 在腳本區塊中的字元數。  
  
 `pas`  
 在此腳本區塊的腳本引擎。  
  
 `fScriptlet`  
 在指出腳本區塊是否為程式碼片段的旗標。  
  
 `pdwSourceContext`  
 脫銷腳本區塊的來源內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 智慧型主機在其檔包含內嵌腳本區塊時，可以使用這個方法。 當語言引擎的程式碼包含適用于其他語言的內嵌腳本時，就可以使用這個方法。  
  
 腳本引擎負責腳本區塊中的所有語法著色和程式碼內容查閱。  
  
 在已加入文字（例如使用 `IDebugDocumentHelper::AddDBCSText` 方法）之後，但在剖析腳本區塊之前，應該呼叫 `DefineScriptBlock` 方法（例如，使用 `IActiveScriptParse ::ParseScriptText` 方法）。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper：： AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)