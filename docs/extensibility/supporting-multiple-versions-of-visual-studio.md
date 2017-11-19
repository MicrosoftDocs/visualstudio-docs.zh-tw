---
title: "支援多個版本的 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc9c13ecf6a5cc6e62caa897adce16830026261a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支援多個版本的 Visual Studio
詞彙*來並行*表示您可以安裝和維護多個版本的同一部電腦上的產品。 適用於 Vspackage，這表示使用者可以擁有數個 Visual Studio 版本安裝在同一部電腦上。 不過，您不能有 Vspackage，載入至單一的 Visual Studio 版本的並存版本。  
  
 VSPackage 可以載入由並行版本的 Visual Studio 之前，請考慮下列各項：  
  
-   您必須決定您想要遵循的來並行實作策略。  
  
     如需詳細資訊，請參閱[選擇之間共用 」 和 「 已建立版本的 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。  
  
-   您的方案和專案檔案的格式必須符合實作策略。  
  
     如需詳細資訊，請參閱[升級自訂專案](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)和[註冊的副檔名來並行部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   您的安裝程式必須處理您實作的策略，以便建立版本的元件，以及所有的版本之間共用的元件已正確安裝並註冊。  
  
     如需詳細資訊，請參閱[與 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)以及[元件管理](../extensibility/internals/component-management.md)。  
  
    > [!NOTE]
    >  安裝 Visual Studio 版本也會安裝對應的版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 例如，在同一部電腦上安裝 Visual Studio 2010 和 Visual Studio 2012 也會安裝 4.0 和 4.5 版[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]分別。  
  
## <a name="in-this-section"></a>本章節內容  
 [在共用和建立版本的 VSPackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 說明如何解決在 VSPackage 中的由並行問題。  
  
 [註冊副檔名以進行並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 描述 VSPackage 如何註冊檔案關聯的並存案例中。  
  
## <a name="related-sections"></a>相關章節  
 [使用 Windows Installer 安裝 VSPackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
