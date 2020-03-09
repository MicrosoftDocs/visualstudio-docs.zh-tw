---
title: 註冊和取消註冊 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409140"
---
# <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 Vspackage
您可以使用屬性來註冊 VSPackage，但是

## <a name="register-a-vspackage"></a>註冊 VSPackage
 您可以使用屬性來控制 managed Vspackage 的註冊。 所有註冊資訊都包含在 *.pkgdef*檔案中。 如需以檔案為基礎之註冊的詳細資訊，請參閱[CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。

 下列程式碼顯示如何使用標準註冊屬性來註冊您的 VSPackage。

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>取消註冊擴充功能
 如果您已經試驗過許多不同的 Vspackage，而且想要從實驗實例中移除它們，您只要執行**Reset**命令即可。 在電腦的 [開始] 頁面上，尋找 [**重設 Visual Studio 實驗實例**]，或從命令列執行此命令：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 如果您想要卸載 Visual Studio 的開發實例上已安裝的擴充功能，請移至 [**工具**] > [**擴充功能和更新**]，尋找擴充功能，然後按一下 [**卸載**]。

 如果基於某些原因，這些方法在卸載擴充功能時都無法成功，您可以從命令列取消註冊 VSPackage 元件，如下所示：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來註冊擴充功能

在某些情況下，您可能需要為您的擴充功能建立新的註冊屬性。 您可以使用註冊屬性來新增登錄機碼，或將新值新增至現有的金鑰。 新的屬性必須衍生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且必須覆寫 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。

### <a name="create-a-custom-attribute"></a>建立自訂屬性

下列程式碼顯示如何建立新的註冊屬性。

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute> 用於屬性類別，以指定屬性所需的程式專案（類別、方法等）、是否可以使用一次以上，以及是否可以繼承。

### <a name="create-a-registry-key"></a>建立登錄機碼

在下列程式碼中，自訂屬性會在要註冊之 VSPackage 的索引鍵底下建立**自訂**子機碼。

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>在現有的登錄機碼下建立新的值

您可以將自訂值新增至現有的金鑰。 下列程式碼示範如何將新值新增至 VSPackage 註冊金鑰。

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
