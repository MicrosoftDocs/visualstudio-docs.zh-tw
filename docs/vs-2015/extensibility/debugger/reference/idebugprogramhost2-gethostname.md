---
title: IDebugProgramHost2::GetHostName |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 420a25be81a124c89bc4139d80ae881b1f519726
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498896"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgramHost2::GetHostName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2-gethostname)。  
  
取得標題、 易記名稱或此程式的裝載處理序的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwType`  
 [in]值，以從[GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列舉型別。  
  
 `pbstrHostName`  
 [out]傳回要求的裝載處理序的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在典型的實作，這個方法，`dwType`參數會被忽略，並傳回主機電腦的易記名稱。 另一個可能的實作是將傳遞`dwType`參數來呼叫[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法來取得名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

