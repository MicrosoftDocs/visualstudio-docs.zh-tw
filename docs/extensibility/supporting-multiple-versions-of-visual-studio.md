---
title: 支援 Visual Studio 的多個版本 |Microsoft Docs
description: 瞭解如何支援多個版本的 Visual Studio，讓您的 Vspackage 能夠載入至不同的版本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52b8bf1be57e10790d91d4712e56d707621cc7df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889937"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支援多個 Visual Studio 版本
此詞彙 *並存* 表示您可以在同一部電腦上安裝和維護產品的多個版本。 針對 Vspackage，這表示使用者可以在同一部電腦上安裝數個 Visual Studio 版本。 不過，您不能將 Vspackage 的並存版本載入 Visual Studio 的單一版本。

 在您將 VSPackage 載入 Visual Studio 的並存版本之前，請考慮下列事項：

- 您必須決定要遵循的並存執行策略。

   如需詳細資訊，請參閱 [在共用和建立版本的 Vspackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。

- 您的解決方案和專案檔案格式必須符合您的執行策略。

   如需詳細資訊，請參閱 [升級自訂專案](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) 和 [註冊並存部署的](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)副檔名。

- 您的安裝程式必須處理您的執行策略，以便正確安裝及註冊已建立版本的元件，以及在所有版本間共用的元件。

   如需詳細資訊，請參閱 [使用 Windows Installer 安裝 vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 以及 [元件管理](../extensibility/internals/component-management.md)。

  > [!NOTE]
  > 安裝 Visual Studio 版本也會安裝對應的 .NET Framework 版本。 例如，在同一部電腦上安裝 Visual Studio 2010 和 Visual Studio 2012，也會分別安裝 .NET Framework 4.0 和4.5 版。

## <a name="in-this-section"></a>本節內容
- [在共用和建立版本的 Vspackage 之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md) 說明如何解決 VSPackage 中並存的問題。

- [註冊並存部署的](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) 副檔名描述 VSPackage 如何在並存案例中註冊檔案關聯。

## <a name="related-sections"></a>相關章節
- [使用 Windows Installer 安裝 VSPackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)
