---
title: 註冊和取消註冊 VS 包 |微軟文檔
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303180"
---
# <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 VS 包
您可以使用屬性註冊 VSPackage，但

## <a name="register-a-vspackage"></a>註冊 VS 包
 您可以使用屬性來控制託管 VSPackages 的註冊。 所有註冊資訊都包含在 *.pkgdef*檔中。 有關基於檔的註冊的詳細資訊，請參閱[CreatePkgDef 實用程式](../extensibility/internals/createpkgdef-utility.md)。

 以下代碼演示如何使用標準註冊屬性來註冊 VSPackage。

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>取消登錄延伸模組
 如果您一直在試驗許多不同的 VSPackages，並希望從實驗實例中刪除它們，則可以運行 **"重置"** 命令。 在電腦的起始頁上查找**重置視覺化工作室實驗實例**，或從命令列運行此命令：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 如果要卸載在 Visual Studio 的開發實例上安裝的擴展，請轉到 **"工具** > **擴展"和"更新**"，查找擴展，然後按一下"**卸載**"。

 如果由於某種原因，這些方法都無法成功卸載擴展，則可以從命令列中取消註冊 VSPackage 程式集，如下所示：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性註冊擴展

在某些情況下，您可能需要為擴展創建新的註冊屬性。 可以使用註冊屬性添加新登錄機碼或向現有鍵添加新值。 新屬性必須派生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，並且必須重寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和 方法<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>。

### <a name="create-a-custom-attribute"></a>建立自訂屬性

以下代碼演示如何創建新的註冊屬性。

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>用於屬性類，以指定屬性相關的程式元素（類、方法等），是否可以多次使用該元素，以及是否可以繼承該元素。

### <a name="create-a-registry-key"></a>創建登錄機碼

在以下代碼中，自訂屬性在正在註冊的 VSPackage 的金鑰下創建**自訂**子鍵。

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>在現有登錄機碼下創建新值

您可以將自訂值添加到現有鍵。 以下代碼演示如何向 VSPackage 註冊金鑰添加新值。

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
