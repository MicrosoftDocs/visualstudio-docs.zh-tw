---
title: 支援多個版本的 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7a1a19cf512d39bce44cfeb1376fdde422f037f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759847"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支援多個 Visual Studio 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

詞彙*並排顯示*表示您可以用來安裝，並維護多個版本的同一部電腦上的產品。 適用於 Vspackage，也就是說，使用者可以擁有數個相同的電腦上安裝的 Visual Studio 版本。 不過，您不能有並排顯示 Vspackage 載入單一版本的 Visual Studio 版本。  
  
 VSPackage 可以載入並排顯示版本的 Visual Studio 之前，請考慮下列各項：  
  
-   您必須決定您想要遵循的並排顯示實作策略。  
  
     如需詳細資訊，請參閱 <<c0> [ 選擇之間共用和建立版本的 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。  
  
-   您的方案和專案檔格式必須符合您的實作策略。  
  
     如需詳細資訊，請參閱 <<c0> [ 升級自訂專案](../misc/upgrading-custom-projects.md)並[並排顯示部署的註冊檔案名稱副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   您的安裝程式必須處理您的實作策略，以便建立版本的元件，以及所有版本，之間共用的元件已正確安裝並註冊。  
  
     如需詳細資訊，請參閱 <<c0> [ 使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)也[元件管理](../extensibility/internals/component-management.md)。  
  
    > [!NOTE]
    >  安裝新版 Visual Studio 也會安裝對應的版本[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。 例如，在相同電腦上安裝 Visual Studio 2010 和 Visual Studio 2012 也會安裝 4.0 和 4.5 版[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]分別。  
  
## <a name="in-this-section"></a>本節內容  
 [在共用和建立版本的 VSPackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 說明如何解決在 VSPackage 中的並排顯示問題。  
  
 [註冊副檔名以進行並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 描述 VSPackage 如何在並排顯示的案例中註冊的檔案關聯。  
  
## <a name="related-sections"></a>相關章節  
 [安裝 VSPackage](../misc/installing-vspackages.md)  
 討論如何建置和安裝 VSPackage，以及如何支援同時執行多個 Visual Studio 版本的使用者。

