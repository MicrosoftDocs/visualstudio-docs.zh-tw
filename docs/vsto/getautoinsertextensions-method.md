---
title: GetAutoInsertExtensions 方法
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
ms.openlocfilehash: 7e3e0fda420682e4f33c0d22a3e9c8caa920895b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671409"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  取得要在偵錯期間會自動插入的 Office 應用程式的相關資訊。  
  
 這個方法是保留供日後使用。  
  
## <a name="syntax"></a>語法  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*psaExtensionNames*|適用於 Office 的應用程式擴充功能名稱。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 每個要插入的 Office 應用程式以 Office 應用程式擴充功能名稱，對應到了下的值傳回**HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**。 主機必須查閱登錄中的這些值，然後再自動插入擴充功能。  
  
  