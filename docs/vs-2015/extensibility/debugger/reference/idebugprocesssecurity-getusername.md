---
title: IDebugProcessSecurity：： GetUserName |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202781"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從埠供應商取得使用者名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrUserName`  
 擴展包含使用者名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `GetUserName`傳回 [**附加至進程**] 對話方塊的 [**使用者名稱**] 欄中所顯示的使用者名稱。 若要查看 [**附加至進程**] 對話方塊，請在整合式開發環境 (IDE) 中，按一下 [**工具**] 功能表上的 [**附加至進程**] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
