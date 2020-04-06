---
title: 支援多個版本的視覺工作室 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699481"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>支援多個 Visual Studio 版本
並排術語*意味著*您可以在同一台電腦上安裝和維護產品的多個版本。 對於 VSPackages,這意味著用戶可以在同一台電腦上安裝多個 Visual Studio 版本。 但是,您不能將 VS 包的並行版本載入到 Visual Studio 的單個版本中。

 在使 VSPackage 能夠載入到並行版本的 Visual Studio 之前,請考慮以下事項:

- 您必須確定要遵循的並行實現策略。

   有關詳細資訊,請參閱[在分享和版本化 VS 套件之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。

- 您的解決方案和專案檔案格式必須適合您的實施策略。

   有關詳細資訊,請參閱[升級自訂項目和](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)[註冊並行部署的檔案名稱副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。

- 安裝程式必須處理實現策略,以便正確安裝和註冊版本控制元件以及跨所有版本共用的元件。

   有關詳細資訊,請參閱[安裝帶有 Windows 安裝程式的 VS 套件](../extensibility/internals/installing-vspackages-with-windows-installer.md)以及[元件管理](../extensibility/internals/component-management.md)。

  > [!NOTE]
  > 安裝 Visual Studio 版本還會安裝相應的 .NET 框架版本。 例如,在同一台電腦上安裝 Visual Studio 2010 和 Visual Studio 2012 也分別安裝 .NET Framework 的 4.0 和 4.5 版本。

## <a name="in-this-section"></a>本節內容
- [在分享與版本化 VS 套件之間進行選擇](../extensibility/choosing-between-shared-and-versioned-vspackages.md)說明如何解決 VS 包中的並排問題。

- [註冊並行部署的檔案名副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)描述 VSPackage 如何在並行方案中註冊文件關聯。

## <a name="related-sections"></a>相關章節
- [使用 Windows Installer 安裝 VSPackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)
