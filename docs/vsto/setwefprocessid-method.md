---
title: "SetWefProcessId 方法 |Microsoft 文件"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd4abab178c951c6150653a1228c2077c5585808
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 方法
  提供將執行 Web 擴充功能架構 (WEF) 內容的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*dwProcessId*|將用來執行 WEF 內容處理序識別碼。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 WEF 內容處理程序建立後，但任何 WEF 內容執行之前，必須呼叫這個方法。  
  
 如果您想要將偵錯工具附加至 WEF 內容處理程序的開發環境，環境就必須實作這個方法中執行此作業。  
  
  