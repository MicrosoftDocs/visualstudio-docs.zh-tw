---
title: "IWebAppDiagnosticsObjectInitialization::Initialize |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsObjectInitialization::Initialize
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32dab78619635f9603fa33794810deef9685a7d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitializationinitialize"></a>IWebAppDiagnosticsObjectInitialization::Initialize
初始化物件以建立[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize(        [in, annotation("__in")] HANDLE_PTR hPassedHandle,        [in, annotation("__in")] IUnknown* pDebugApplication        );  
```  
  
#### <a name="parameters"></a>參數  
 `hPassedHandle`  
 控制代碼傳遞給[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)方法中的`hPassToObject`參數。  
  
 `pDebugApplication`  
 建立物件所使用的 PDM 應用程式。