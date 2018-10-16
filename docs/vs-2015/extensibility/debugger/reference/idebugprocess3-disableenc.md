---
title: IDebugProcess3::DisableENC |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b14019d94f322f8822825477e18d60c0a54490c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192136"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法明確地停用編輯後繼續在此程序 （和它包含的所有程式）。 自訂連接埠供應商應該一律傳回`E_NOTIMPL`。  
  
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
 [in]值，以從[EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。  
  
> [!NOTE]
>  自訂連接埠供應商應該一律傳回`E_NOTIMPL`。  
  
## <a name="remarks"></a>備註  
 一次編輯後繼續 會停用處理程序，可以只藉由重新啟動處理程序重新啟用。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

