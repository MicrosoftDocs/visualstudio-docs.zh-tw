---
title: "IDebugProcess3::DisableENC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::DisableENC
helpviewer_keywords: IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fed5f54c843732b45339d7cc37d7d0820a58d8a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
這個方法明確地停用編輯後繼續在此程序 （和它包含的所有程式）。 自訂連接埠供應商應該會一律傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>參數  
 `reason`  
 [in]中的值[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
> [!NOTE]
>  自訂連接埠供應商應該會一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
 一次編輯後繼續已停用的處理程序，可以只是藉由重新啟動處理程序重新啟用。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)