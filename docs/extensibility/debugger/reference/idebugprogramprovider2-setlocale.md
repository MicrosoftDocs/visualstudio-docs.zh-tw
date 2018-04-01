---
title: IDebugProgramProvider2::SetLocale |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fa3bbadd4266466d18fbd24cee83ec916aa571ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
建立要用於任何地區設定特定資源的地區設定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wLangID`  
 [in]若要建立語言識別碼。 例如，1033 代表英文。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)