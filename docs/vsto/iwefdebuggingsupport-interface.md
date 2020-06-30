---
title: IWefDebuggingSupport 介面
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544725"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport 介面
  由偵錯工具（例如 Visual Studio）來執行，以加速對 Office 應用程式的偵測。 Office 應用程式（例如 Word 或 Excel）會從 Visual Studio 取得這個介面，然後在偵錯工具期間的特定點上呼叫介面上的方法。

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
 下表列出 IWefDebuggingSupport 介面所定義的方法。

|名稱|描述|
|----------|-----------------|
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|取得要在偵測期間自動插入之 Office 應用程式的相關資訊。|
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供將執行 Web Extensions Framework （WEF）內容的處理序識別碼。|
