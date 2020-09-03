---
title: IDebugDocumentPositionOffset2：： GetRange |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200226"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

抓取目前檔位置的範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwBegOffset`  
 [in，out]範圍開始位置的位移。 如果不需要這項資訊，請將此參數設定為 null 值。  
  
 `pdwEndOffset`  
 [in，out]範圍結束位置的位移。 如果不需要這項資訊，請將此參數設定為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 偵錯工具引擎會使用位置中斷點的檔位置所指定的範圍 (DE) 來向前搜尋實際提供程式碼的語句。 例如，請參考下列程式碼：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第5行對要進行調試的程式沒有任何程式碼。 如果在第5行設定中斷點的偵錯工具想要取消搜尋提供程式碼的第一行，偵錯工具會指定一個範圍，其中包含可能正確放置中斷點的其他候選行。 然後，會向前搜尋這些行，直到找到可接受中斷點的行為止。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
