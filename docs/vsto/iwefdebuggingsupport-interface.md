---
title: IWefDebuggingSupport 介面
description: 瞭解如何使用類似 Visual Studio 的偵錯工具，以加速 Microsoft Office 應用程式的偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fc319429414c8976d748a30ecdd1e164ce22b63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962258"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport 介面
  由偵錯工具（例如 Visual Studio）所執行，可協助您對 Office 的應用程式進行偵錯工具。 Office 應用程式（例如 Word 或 Excel）會從 Visual Studio 取得這個介面，然後在偵錯工具期間的特定時間點呼叫介面上的方法。

## <a name="syntax"></a>Syntax

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
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|取得要在進行偵錯工具時自動插入的 Office 相關應用程式的相關資訊。|
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供將執行 Web Extensions Framework (WEF) 內容的處理序識別碼。|
