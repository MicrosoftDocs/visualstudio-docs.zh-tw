---
title: "GetAutoInsertExtensions 方法 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d222f7b6751381ceb4ebdb27bb6a6bf223616df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  取得要在偵錯期間自動插入的 Office 應用程式的相關資訊。  
  
 這個方法是保留供日後使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|*psaExtensionNames*|適用於 Office 的應用程式的延伸模組名稱。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 適用於 Office 插入每個應用程式會當成對應至值 HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer 下的 Office 應用程式擴充功能名稱。 主機必須查閱登錄中的這些值，並自動插入擴充功能。  
  
  