---
title: "條件式編譯變數 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-variables-javascript"></a>條件式編譯變數 (JavaScript)
以下預先定義的變數可供條件式編譯使用。 如果變數不是 **true**，則表示變數未定義，並且在存取時的行為會是 `NaN`。  
  
> [!WARNING]
>  Internet Explorer 11 以前的所有 Internet Explorer 版本都支援條件式編譯。 從 Internet Explorer 11 標準模式開始以及在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式中，都不支援條件式編譯。  
  
## <a name="variables"></a>變數  
  
|變數|說明|  
|--------------|-----------------|  
|@_win32|如果在 Win32 系統上執行則為 True。|  
|@_win16|如果在 Win16 系統上執行則為 True。|  
|@_mac|如果在 Apple Macintosh 系統上執行則為 True。|  
|@_alpha|如果在 DEC Alpha 處理器上執行則為 True。|  
|@_x86|如果在 Intel 處理器上執行則為 True。|  
|@_mc680x0|如果在 Motorola 680x0 處理器上執行則為 True。|  
|@_PowerPC|如果在 Motorola PowerPC 處理器上執行則為 True。|  
|@_jscript|一定是 true。|  
|@_jscript_build|包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 指令碼引擎的組建編號。|  
|@_jscript_version|包含 major.minor 格式的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本號碼。|