---
title: EnsureVSTOComponent 函式
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08b22ed86851a35f23306fc765f62f265da4701e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671203"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 函式
  此 API 支援 Office 基礎結構，但不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```csharp  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*pProject*|請勿使用。|  
  
## <a name="return-value"></a>傳回值  
 如果此函數就會成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  
  
  