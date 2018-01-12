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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
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
  
|參數|描述|  
|---------------|-----------------|  
|*psaExtensionNames*|適用於 Office 的應用程式的延伸模組名稱。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 適用於 Office 插入每個應用程式會當成對應至值 HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer 下的 Office 應用程式擴充功能名稱。 主機必須查閱登錄中的這些值，並自動插入擴充功能。  
  
  