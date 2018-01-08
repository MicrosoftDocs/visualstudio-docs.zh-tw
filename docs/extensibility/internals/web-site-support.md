---
title: "網站支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b43963d657e8d1fe7aa24e98632d2ca46240c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support"></a>網站支援
網站專案系統會建立 Web 專案的專案系統。 Web 專案建立 Web 應用程式。 網站專案會產生一個可執行檔，每個具有相關聯的程式碼的網頁。 從原始程式碼檔案 /App_Code 資料夾中產生其他可執行檔。  
  
 網站專案系統會將範本和註冊屬性加入至現有的專案系統建立。 這些屬性的其中一個選取的語言，IntelliSense 提供者。 IntelliSense 提供者實作處理的參考，並不會快取智慧網頁的要求時所呼叫的語言編譯器。  
  
 用來編譯網頁的語言編譯器必須向[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]。 您可以使用[\<編譯器 > 項目](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element)来登錄的編譯器，如下列範例所示的 Web.config 檔案中：  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>本節內容  
 [網站支援範本](../../extensibility/internals/web-site-support-templates.md)  
 列出可用來建立新的網站專案和相關聯的項目範本。  
  
 [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)  
 顯示連接到網站專案的登錄屬性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]。  
  
## <a name="related-sections"></a>相關章節  
 [Web 專案](../../extensibility/internals/web-projects.md)  
 提供兩個這類 Web 專案的網站專案及 Web 應用程式專案的概觀。