---
title: 支援 Visual Studio 2015 的多重版本 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838770"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支援多個 Visual Studio 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此詞彙 *並存* 表示您可以在同一部電腦上安裝和維護產品的多個版本。 針對 Vspackage，這表示使用者可以在同一部電腦上安裝數個 Visual Studio 版本。 不過，您不能將 Vspackage 的並存版本載入 Visual Studio 的單一版本。

 在您將 VSPackage 載入 Visual Studio 的並存版本之前，請考慮下列事項：

- 您必須決定要遵循的並存執行策略。

     如需詳細資訊，請參閱 [在共用和建立版本的 Vspackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。

- 您的解決方案和專案檔案格式必須符合您的執行策略。

     如需詳細資訊，請參閱 [升級自訂專案](../misc/upgrading-custom-projects.md) 和 [註冊並存部署的](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)副檔名。

- 您的安裝程式必須處理您的執行策略，以便正確安裝及註冊已建立版本的元件，以及在所有版本間共用的元件。

     如需詳細資訊，請參閱 [使用 Windows Installer 安裝 vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 以及 [元件管理](../extensibility/internals/component-management.md)。

    > [!NOTE]
    > 安裝某個版本的 Visual Studio 也會安裝對應的版本 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 例如，在同一部電腦上安裝 Visual Studio 2010 和 Visual Studio 2012，也會分別安裝4.0 和4.5 版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="in-this-section"></a>本節內容
 [在共用和建立版本的 Vspackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md) 說明如何解決 VSPackage 中並存的問題。

 [註冊並存部署的](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) 副檔名描述 VSPackage 如何在並存案例中註冊檔案關聯。

## <a name="related-sections"></a>相關章節
 [安裝 vspackage](../misc/installing-vspackages.md) 討論如何建立和安裝 Vspackage，以及如何支援同時執行多個版本 Visual Studio 的使用者。
