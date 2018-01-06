---
title: "IWefDebuggingSupport 介面 |Microsoft 文件"
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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 150c8794fb35ca017be7e0873dc0d1b84ebfc38c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport 介面
  藉由偵錯環境，例如 Visual Studio 中，以協助偵錯 office 應用程式。 Office 應用程式，例如 Word 或 Excel，從 Visual Studio 中取得此介面，，然後在偵錯工作階段的特定時間點的介面上呼叫方法。  
  
## <a name="syntax"></a>語法  
  
```  
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
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|取得要在偵錯期間自動插入的 Office 應用程式的相關資訊。|  
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供將執行 Web 擴充功能架構 (WEF) 內容的處理序識別碼。|  
  
  