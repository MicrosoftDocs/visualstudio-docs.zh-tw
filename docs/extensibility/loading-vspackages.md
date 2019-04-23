---
title: 載入 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce0f09c1749621838729e1e4f64feb3ca8b07628
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117560"
---
# <a name="load-vspackages"></a>載入 Vspackage
Vspackage 會載入到 Visual Studio 中，只有需要其功能時，只有。 比方說，Visual Studio 使用專案 factory 或 VSPackage 實作的服務時，會載入 VSPackage。 這項功能稱為延遲的載入，這會盡可能以改善效能。

> [!NOTE]
>  Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供，而不必載入 VSPackage 的命令。

 Vspackage 可以例如設定自動載入在特定的使用者介面 (UI) 內容中，開啟方案時。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性會設定此內容。

### <a name="autoload-a-vspackage-in-a-specific-context"></a>自動載入 VSPackage 中特定的內容

- 新增`ProvideAutoLoad`屬性加入 VSPackage 屬性：

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     請參閱列舉的欄位<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>如 UI 內容和其 GUID 值的清單。

- 在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。

- 建置 VSPackage，並開始偵錯。

- 載入方案或建立一個。

     VSPackage 載入，並在中斷點停止。

## <a name="force-a-vspackage-to-load"></a>強制載入 VSPackage
 在某些情況下 VSPackage 可能必須強制另一個要載入的 VSPackage。 比方說，輕量級 VSPackage 可能會載入較大的 VSPackage，不是 CMDUIContext 可用的內容中。

 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>方法，以強制載入 VSPackage。

- 插入此程式碼<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>的 VSPackage，強制載入的另一個 VSPackage 的方法：

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     初始化 VSPackage 時，它會強制`PackageToBeLoaded`載入。

     強制載入不應該用於 VSPackage 通訊。 使用[使用，並提供服務](../extensibility/using-and-providing-services.md)改。

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
