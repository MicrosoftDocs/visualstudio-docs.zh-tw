---
title: "IDebugDocumentHelper::DefineScriptBlock |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
指出特定範圍的字元是由指定的指令碼引擎所處理的指令碼區塊協助程式。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]指令碼區塊的開始位置。  
  
 `cChars`  
 [in]指令碼區塊中的字元數。  
  
 `pas`  
 [in]此指令碼區塊的指令碼引擎。  
  
 `fScriptlet`  
 [in]旗標，指出指令碼區塊是否為程式碼片段。  
  
 `pdwSourceContext`  
 [out]指令碼區塊的來源內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 智慧主機可以使用這個方法，當其文件包含內嵌指令碼區塊。 語言引擎其程式碼包含內嵌的指令碼的其他語言時，可以使用這個方法。  
  
 指令碼引擎負責所有語法著色和程式碼內容查閱指令碼區塊中。  
  
 `DefineScriptBlock`新增文字之後，應該呼叫方法 (例如，使用`IDebugDocumentHelper::AddDBCSText`方法) 已剖析之前的指令碼區塊，但 (比方說，使用`IActiveScriptParse ::ParseScriptText`方法)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)