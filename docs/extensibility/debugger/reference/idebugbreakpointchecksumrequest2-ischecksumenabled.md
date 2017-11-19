---
title: "IDebugBreakpointChecksumRequest2::IsChecksumEnabled |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7386ab585ac054e40e08ff2e4cf5f5d84fe8ab30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
判斷是否啟用此文件的總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```csharp  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfChecksumEnabled`  
 [out]如果已啟用總和檢查碼; 為 true，則傳回反之則傳回 FALSE。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)