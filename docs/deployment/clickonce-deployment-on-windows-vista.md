---
title: "Windows Vista 的 ClickOnce 部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 49ea73293e8cc491b515644a7e7d3f226a799339
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista 的 ClickOnce 部署
在 Visual Studio 中的建置應用程式對使用者帳戶控制 (UAC) 在 Windows Vista 上通常會產生內嵌的資訊清單，編碼為二進位的 XML 資料，應用程式的可執行檔。 因為 ClickOnce 和免註冊 COM 應用程式需要外部資訊清單，Visual Studio 會產生這些類型的專案包含 UAC 資料，而不是內嵌的資訊清單檔案。 根據預設，Visual Studio 會從呼叫 app.manifest 檔案使用資訊，來產生外部 UAC 資訊清單資訊 （如 ClickOnce 和免註冊 COM 部署），或將它內嵌在應用程式的可執行檔 （適用於所有其他情況下）。 Visual Studio 提供下列選項以產生資訊清單：  
  
-   使用內嵌的資訊清單。 UAC 將資料內嵌在應用程式的可執行檔並以一般使用者身分執行。  
  
     （除非您使用 ClickOnce），這是預設設定。 這項設定將在 Windows Vista; 上支援 Visual Studio 運作方式的一般方式也就是說，內部和外部資訊清單，這兩個使用產生`AsInvoker`。  
  
-   使用外部資訊清單。 使用資訊清單產生外部資訊清單。  
  
     這是藉由使用資訊清單中的資訊產生外部資訊清單。 當您使用 ClickOnce 或免註冊 COM 發行應用程式時，Visual Studio 會將資訊清單加入專案，並將此選項。  
  
-   使用不到資訊清單。 建立無資訊清單應用程式。  
  
     這個方法就是所謂*虛擬化*。 使用此選項與現有的應用程式從舊版的 Visual Studio 的相容性。  
  
 新的屬性值可用於**應用程式**頁面的 專案設計工具 （Visual C# 專案只） 在 MSBuild 專案檔格式。  
  
 請注意，在 Visual Studio IDE 中設定 UAC 資訊清單產生的方法會根據專案類型 （Visual C# 和 Visual Basic） 而不同。  
  
 設定 Visual C# 專案，以產生資訊清單的相關資訊，請參閱[應用程式] 頁面上，[專案設計工具 (C#)](../ide/reference/application-page-project-designer-csharp.md)。  
  
 設定 Visual Basic 專案，以產生資訊清單的相關資訊，請參閱[應用程式] 頁面上，[專案設計工具 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [使用者權限和 Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)