---
title: "IDebugDocumentPositionOffset2::GetRange |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65ae083dcc744f93948c03c6dfb3cd37ce265701
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
擷取目前的文件位置的範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in、 out]範圍的開始位置的位移。 如果不需要這項資訊，請設定此參數為 null 值。  
  
 `pdwEndOffset`  
 [in、 out]範圍的結束位置的位移。 如果不需要這項資訊，請設定此參數為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 位置中斷點的文件位置中指定的範圍可由偵錯引擎 (DE) 來繼續搜尋實際上提供程式碼陳述式。 例如，請參考下列程式碼：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行是計算任何程式碼進行偵錯的程式。 如果在第 5 行上設定中斷點，偵錯工具要向前搜尋特定量佔程式碼的第一行 DE，偵錯工具會指定包含其他候選項目行中斷點可能會正確地放置範圍。 DE 會再向前搜尋這些行直到它找到無法接受中斷點的該行。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)