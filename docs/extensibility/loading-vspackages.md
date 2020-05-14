---
title: 正在載入 VS 套件 |微軟文件
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
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702958"
---
# <a name="load-vspackages"></a>載入 VS 套件
僅當需要 VS 包的功能時,才會載入到 Visual Studio 中。 例如,當 Visual Studio 使用專案工廠或 VSPackage 實現的服務時,將載入 VS 包。 此功能稱為延遲載入,盡可能用於提高性能。

> [!NOTE]
> Visual Studio 可以確定某些 VSPackage 資訊,例如 VSPackage 提供的命令,而無需載入 VSPackage。

 VS包可以設置為在特定使用者介面 (UI) 上下文中自動載入,例如,當解決方案打開時。 屬性<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>設置此上下文。

### <a name="autoload-a-vspackage-in-a-specific-context"></a>在特定內容自動載入 VS 套件

- 將`ProvideAutoLoad`屬性加入 VSPackage 屬性:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     有關 UI 上下<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>文及其 GUID 值的清單,請參閱 的枚舉欄位。

- 在<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法中設置斷點。

- 生成 VS 包並開始調試。

- 載入解決方案或創建解決方案。

     VSPackage 在斷點載入和停止。

## <a name="force-a-vspackage-to-load"></a>強制 VS 套件載入
 在某些情況下,VSPackage 可能必須強制載入另一個 VSPackage。 例如,輕巧 VS 套件可能會在無法作為 CMDUIContext 提供的上下文中載入較大的 VS 包。

 可以使用方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>強制載入 VSPackage。

- 將此代碼插入<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>VSPackage 的方法,該方法強制另一個 VSPackage 載入:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     初始化 VSPackage 時,它`PackageToBeLoaded`將強制 載入。

     力載入不應用於 VSPackage 通信。 而是[使用與提供服務](../extensibility/using-and-providing-services.md)。

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
