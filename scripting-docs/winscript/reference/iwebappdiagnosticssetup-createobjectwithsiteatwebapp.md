---
title: IWebAppDiagnosticsSetup：： CreateObjectWithSiteAtWebApp |Microsoft Docs
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
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984599"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
這個方法會共同建立類別，您可以使用 `dwClsContext`將其識別碼傳入 `rclsid`。 這類似于[IRemoteDebugApplication：： CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)的運作方式，不同的是，在 `CreateObjectWithSiteAtWebApp` 的情況下，物件是在 web 應用程式的 UI 執行緒上以非同步方式建立的。 類別識別碼所指定的物件應該執行[IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。 建立物件之後，會使用 PDM debug 應用程式的參考和 `CreateObjectWithSiteAtWebApp`的 `hPassToObject` 參數來呼叫[IWebAppDiagnosticsObjectInitialization：： Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 。 您可以使用這個方法，將您使用[DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)複製之匿名管道的控制碼傳入應用程式。  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 要建立之類別的類別 ID。  
  
 `dwClsContext`  
 將在其中執行程式碼的內容。 在大部分情況下，它是 CLSCTX_INPROC_SERVER。  
  
 `riid`  
 未使用。  
  
 `hPassToObject`  
 在 UI 執行緒上建立物件後，如果物件會執行[IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)，則會傳遞至物件的值。