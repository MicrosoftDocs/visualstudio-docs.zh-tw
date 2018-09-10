---
title: Windows Vista 的 ClickOnce 部署 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 815186959d4a8cd1daea46c69bda976eb4483c1f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282582"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista 的 ClickOnce 部署

在 Visual Studio 中的建置應用程式的使用者帳戶控制 (UAC) 在 Windows Vista 上通常會產生的內嵌資訊清單中，編碼為二進位的 XML 資料，在應用程式的可執行檔。  ClickOnce 和免註冊 COM 應用程式需要的外部的資訊清單，因此 Visual Studio 會產生這些專案包含 UAC 資料，而不是內嵌的資訊清單的檔案。 ClickOnce 和免註冊 COM 部署 Visual Studio 會使用資訊檔案，稱為*app.manifest*產生外部 UAC 資訊清單資訊。 所有其他情況下，Visual Studio 會將 UAC 資料內嵌在應用程式的可執行檔。 

Visual Studio 會提供下列選項，以產生資訊清單：  
  
-   使用內嵌資訊清單。 在應用程式的可執行檔中內嵌 UAC 資料，並以一般使用者身分執行。  
  
     （除非您使用 ClickOnce 時），這是預設設定。 此設定支援在 Windows Vista 上的 Visual Studio 運作方式的一般方式，與內部和外部的產生資訊清單使用`AsInvoker`。  
  
-   使用外部資訊清單。 使用產生的外部資訊清單*app.manifest*。  
  
     這會將外部資訊清單產生使用中的資訊*app.manifest*。 當您發行應用程式使用 ClickOnce 或免註冊 COM 時，Visual Studio 會加入*app.manifest*至專案，然後新增此選項。  
  
-   使用任何資訊清單。 建立無資訊清單應用程式。  
  
     這種方法就是所謂*虛擬化*。 使用此選項，與現有的應用程式從舊版的 Visual Studio 的相容性。  
  
 新的屬性值可用於**應用程式**頁面的 專案設計工具 （Visual C# 中僅限專案） 和 MSBuild 專案檔案格式。  
  
 Visual Studio IDE 中設定 UAC 資訊清單產生的方法需視專案類型 （Visual C# 或 Visual Basic） 而有所不同。  
  
   * 如需設定 Visual C# 專案，以產生資訊清單資訊，請參閱 < [Application Page，Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)。  
  
   * 如需設定 Visual Basic 專案以產生資訊清單資訊，請參閱 < [Application Page，Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [使用者權限和 Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)