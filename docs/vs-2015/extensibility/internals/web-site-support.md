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
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687686"
---
# <a name="web-site-support"></a>網站支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

網站專案系統是建立 Web 專案的專案系統。 Web 專案接著會建立 Web 應用程式。 網站專案會為每個具有相關程式碼的網頁產生一個可執行檔。 其他可執行檔是從/App_Code 資料夾中的原始程式碼檔產生的。  
  
 網站專案系統的建立方式，是將範本和註冊屬性新增至現有的專案系統。 其中一個屬性會選取語言的 IntelliSense 提供者。 當要求未快取的智慧型網頁時，IntelliSense 提供者的執行會處理參考並呼叫語言編譯器。  
  
 用來編譯網頁的語言編譯器必須向註冊 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 。 您可以使用 Web.config 檔案中的[ \<compiler> 元素](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823)來註冊編譯器，如下列範例所示：  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>本節內容  
 [網站支援範本](../../extensibility/internals/web-site-support-templates.md)  
 列出您可以用來建立新網站專案和相關專案的範本。  
  
 [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)  
 提供連接到和的網站專案的註冊屬性 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 。  
  
## <a name="related-sections"></a>相關章節  
 [Web 專案](../../extensibility/internals/web-projects.md)  
 提供兩種 Web 專案、網站專案和 Web 應用程式專案的總覽。
