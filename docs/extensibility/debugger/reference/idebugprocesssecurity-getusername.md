---
title: "IDebugProcessSecurity::GetUserName |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 909c4b4e47bdc9de60b9761974843b370c7400e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
從連接埠供應商取得的使用者名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]字串，包含使用者名稱。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `GetUserName`傳回中所顯示的使用者名稱**使用者名**資料行**附加至處理序** 對話方塊。 若要檢視**附加至處理序**對話方塊中，按一下 **附加至處理序**上**工具**功能表[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)