---
title: IWefDebuggingSupport 介面
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
ms.openlocfilehash: 55a09c3db9a47b5bcf22a7faeb891a1f709d244a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865680"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport 介面
  由偵錯的環境中，為了方便偵錯的應用程式，適用於 Office 的 Visual Studio 這類實作。 Office 應用程式，例如 Word 或 Excel，從 Visual Studio 中取得這個介面，，然後在偵錯工作階段的特定時間點在介面上呼叫方法。  
  
## <a name="syntax"></a>語法  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>方法  
 下表列出 IWefDebuggingSupport 介面定義的方法。  
  
|名稱|描述|  
|----------|-----------------|  
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|取得要在偵錯期間會自動插入的 Office 應用程式的相關資訊。|  
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供將執行 Web 擴充功能架構 (WEF) 內容的處理序識別碼。|  
