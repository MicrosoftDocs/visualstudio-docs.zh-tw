---
title: 正在載入 Vspackage |Microsoft Docs
description: 瞭解如何在 Visual Studio 中載入 Vspackage，包括延遲載入，這會在可能的情況下用來改善效能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aeab78a2f64be2df6f601ad8ed224f13071eb8c
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616100"
---
# <a name="load-vspackages"></a>Load Vspackage
Vspackage 只有在需要它們的功能時，才會載入 Visual Studio。 例如，當 Visual Studio 使用專案 factory 或 VSPackage 所執行的服務時，就會載入 VSPackage。 這項功能稱為延遲載入，會盡可能用來改善效能。

> [!NOTE]
> Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供的命令，而不需要載入 VSPackage。

 Vspackage 可以設定為特定使用者介面中的自動載入， (UI) 內容，例如開啟方案時。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性會設定此內容。

### <a name="autoload-a-vspackage-in-a-specific-context"></a>在特定內容中自動載入 VSPackage

- 將 `ProvideAutoLoad` 屬性新增至 VSPackage 屬性：

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>如需 UI 內容和其 GUID 值清單的詳細資料，請參閱的列舉欄位。

- 在方法中設定中斷點 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 。

- 建立 VSPackage 並開始進行調試。

- 載入解決方案或建立一個。

     VSPackage 會在中斷點載入並停止。

## <a name="force-a-vspackage-to-load"></a>強制載入 VSPackage
 在某些情況下，VSPackage 可能必須強制載入另一個 VSPackage。 例如，輕量 VSPackage 可能會在無法以 CMDUICoNtext 形式提供的內容中載入較大的 VSPackage。

 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> 方法強制載入 VSPackage。

- 將此程式碼插入 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackage 的方法中，以強制載入另一個 VSPackage：

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     當 VSPackage 初始化時，它將會強制 `PackageToBeLoaded` 載入。

     不應使用強制載入來進行 VSPackage 通訊。 請改用 [使用並提供服務](../extensibility/using-and-providing-services.md) 。

## <a name="see-also"></a>另請參閱
- [VSPackages](../extensibility/internals/vspackages.md)
