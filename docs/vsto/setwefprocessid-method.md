---
title: SetWefProcessId 方法
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7807d0495c5f0548178b1bc2ecae12d57cc3b072
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876118"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 方法
  提供將執行 Web 擴充功能架構 (WEF) 內容的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*dwProcessId*|將用來執行 WEF 內容的處理序識別碼。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 建立 WEF 內容處理程序之後，但任何 WEF 內容執行之前，必須呼叫這個方法。  
  
 如果您想要將偵錯工具附加至 WEF 內容處理程序的開發環境，環境就必須實作這個方法中執行此作業。  
