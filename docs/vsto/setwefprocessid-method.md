---
title: SetWefProcessId 方法 |Microsoft 文件
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
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
  
  