---
title: Windows Vista 的 ClickOnce 部署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675467"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista 的 ClickOnce 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中的建置應用程式的使用者帳戶控制 (UAC) 在 Windows Vista 上通常會產生的內嵌資訊清單中，編碼為二進位的 XML 資料，在應用程式的可執行檔。 ClickOnce 和免註冊 COM 的應用程式需要的外部資訊清單，因為 Visual Studio 會產生這些類型的專案包含 UAC 資料，而不是內嵌的資訊清單的檔案。 根據預設，Visual Studio 會從名為 app.manifest 檔案使用資訊，以產生外部 UAC 資訊清單資訊 （用於 ClickOnce 和免註冊 COM 部署），或將它內嵌在應用程式的可執行檔 （適用於所有其他情況下）。 Visual Studio 會提供下列選項，以產生資訊清單：  
  
- 使用內嵌資訊清單。 在應用程式的可執行檔中內嵌 UAC 資料，並以標準使用者身分執行。  
  
   （除非您使用 ClickOnce 時），這是預設設定。 這項設定將支援在 Windows Vista; 上的 Visual Studio 運作方式的一般方式也就是產生的內部和外部資訊清單中，這兩個使用`AsInvoker`。  
  
- 使用外部資訊清單。 使用 app.manifest 中產生外部資訊清單。  
  
   這是藉由使用 app.manifest 中的資訊產生外部資訊清單。 當您發行應用程式使用 ClickOnce 或免註冊 COM 時，Visual Studio 專案中新增 app.manifest，並將此選項。  
  
- 使用任何資訊清單。 建立無資訊清單應用程式。  
  
   這種方法就是所謂*虛擬化*。 使用此選項，與現有的應用程式從舊版的 Visual Studio 的相容性。  
  
  新的屬性值可用於**應用程式**頁面的 專案設計工具 （Visual C# 中僅限專案） 和 MSBuild 專案檔案格式。  
  
  請注意，Visual Studio IDE 中設定 UAC 資訊清單產生的方法將視專案類型 （Visual C# 和 Visual Basic） 而有所不同。  
  
  如需設定 Visual C# 專案，以產生資訊清單資訊，請參閱 < [Application Page，Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)。  
  
  如需設定 Visual Basic 專案以產生資訊清單資訊，請參閱 < [Application Page，Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [使用者權限和 Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
