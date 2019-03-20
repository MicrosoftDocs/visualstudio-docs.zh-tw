---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76b3a3b4c1cbc3c5f3e9c3fddaca2be79d3f5851
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156303"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
判斷此應用程式是否支援診斷。 如果[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)已經實作了非 NULL 值，這個介面的物件上呼叫[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)傳回`true`。 如果沒有，它會傳回`false`並呼叫[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md)是實作由 PDM v11.0 和更新版本。 在 activdbg100 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 如果[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)已經實作了非 NULL 值，這個介面的物件上呼叫[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)傳回`true`。 如果沒有，它會傳回`false`，並呼叫[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗。