---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26403a168268e817644637544d64d4205c398b75
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157655"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
這個方法會同時建立類別識別碼中使用您傳遞`rclsid`使用`dwClsContext`。 這是類似的方式[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)運作方式，只不過是`CreateObjectWithSiteAtWebApp`web 應用程式的 UI 執行緒上以非同步方式建立物件。 類別識別碼所指定的物件應該實作[IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。 在建立物件之後， [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)稱為 PDM 偵錯應用程式的參考並`hPassToObject`參數`CreateObjectWithSiteAtWebApp`。 您可以使用這個方法在應用程式將控制代碼傳遞至您複製使用匿名管道[DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 若要建立類別的類別 ID。  
  
 `dwClsContext`  
 程式碼將在其中執行內容。 在大部分情況下，它會是 CLSCTX_INPROC_SERVER。  
  
 `riid`  
 未使用。  
  
 `hPassToObject`  
 值，將傳遞至該物件建立後即在 UI 執行緒，如果物件實作[IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。