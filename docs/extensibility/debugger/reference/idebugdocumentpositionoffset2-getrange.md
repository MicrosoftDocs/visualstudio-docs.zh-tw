---
title: IDebugDocumentPositionOffset2::GetRange |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70f878c7299ab716c764f5962d675691f4bb521a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860106"
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
 [in、 out]範圍的起始位置的位移。 如果不需要這項資訊，請設定此參數為 null 值。  
  
 `pdwEndOffset`  
 [in、 out]範圍的結束位置的位移。 如果不需要這項資訊，請設定此參數為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 位置中斷點的文件位置中指定的範圍由偵錯引擎 (DE) 用於實際提供的程式碼的陳述式繼續搜尋。 例如，請參考下列程式碼：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行貢獻到程式正在偵錯任何程式碼。 如果在第 5 行設定中斷點的偵錯工具想要向前搜尋特定數量的貢獻程式碼的第一行 DE，偵錯工具會指定包含其他候選項目行中斷點可能會正確地放置範圍。 DE 會再向前搜尋這些行直到它找到可以接受中斷點的該行。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)