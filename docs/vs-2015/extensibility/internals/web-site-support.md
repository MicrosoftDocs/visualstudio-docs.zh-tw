---
title: 網站支援 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91deb6d2e3ec58533ac9339c8c94634db23ec996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946011"
---
# <a name="web-site-support"></a>網站支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

網站專案系統會建立 Web 專案的專案系統。 Web 專案接著會建立 Web 應用程式。 網站專案產生一個可執行檔的檔案，每個網頁相關聯的程式碼。 從存放在 /App_Code 資料夾的原始程式碼檔產生額外的可執行檔。  
  
 網站專案系統會將範本和註冊屬性加入至現有的專案系統建立。 這些屬性的其中一個選取的語言的 IntelliSense 提供者。 IntelliSense 提供者實作會處理參考，並不會快取智慧網頁的要求時所呼叫的語言編譯器。  
  
 用來編譯網頁的語言編譯器必須向[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]。 您可以使用[\<編譯器 > 項目](http://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823)在 Web.config 檔註冊的編譯器，如下列範例所示：  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>本節內容  
 [網站支援範本](../../extensibility/internals/web-site-support-templates.md)  
 列出可用來建立新的網站專案和相關聯的項目範本。  
  
 [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)  
 提供連線至網站專案的登錄屬性[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]和[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]。  
  
## <a name="related-sections"></a>相關章節  
 [Web 專案](../../extensibility/internals/web-projects.md)  
 提供兩種 Web 專案、 網站專案和 Web 應用程式專案的概觀。
