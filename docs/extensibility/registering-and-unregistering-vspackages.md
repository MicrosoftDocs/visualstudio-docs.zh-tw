---
title: 註冊和取消註冊 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f345bdbd3cf5858d495937c743b580abf5e3dd50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701586"
---
# <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 Vspackage
您可以使用屬性來註冊 VSPackage，但是

## <a name="register-a-vspackage"></a>註冊 VSPackage
 您可以使用屬性來控制受控 Vspackage 的註冊。 所有註冊資訊都包含在 *.pkgdef* 檔案中。 如需以檔案為基礎之註冊的詳細資訊，請參閱 [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。

 下列程式碼說明如何使用標準註冊屬性來註冊您的 VSPackage。

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>取消登錄延伸模組
 如果您已經試驗過許多不同的 Vspackage，而且想要從實驗性實例中移除它們，您可以直接執行 **Reset** 命令。 在電腦的 [開始] 頁面上尋找 **[重設 Visual Studio 實驗實例** ]，或從命令列執行下列命令：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 如果您想要卸載 Visual Studio 開發實例上安裝的擴充功能，請移至 [**工具**  >  **擴充功能和更新**]，尋找擴充功能，然後按一下 [**卸載**]。

 如果基於某些原因，這兩種方法都無法在卸載擴充功能的情況下成功，您可以從命令列取消註冊 VSPackage 元件，如下所示：

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來註冊擴充功能

在某些情況下，您可能需要為您的延伸模組建立新的註冊屬性。 您可以使用註冊屬性來新增新的登錄機碼，或將新的值新增至現有的金鑰。 新的屬性必須衍生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，而且必須覆寫 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。

### <a name="create-a-custom-attribute"></a>建立自訂屬性

下列程式碼顯示如何建立新的註冊屬性。

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>會在屬性類別上用來指定 (類別、方法等 ) 的程式元素、屬性所的專案，是否可以使用一次以上，以及是否可以繼承。

### <a name="create-a-registry-key"></a>建立登錄機碼

在下列程式碼中，自訂屬性會在要註冊的 VSPackage 機碼底下建立 **自訂** 子機碼。

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>在現有的登錄機碼底下建立新的值

您可以將自訂值新增至現有的索引鍵。 下列程式碼示範如何將新值新增至 VSPackage 註冊金鑰。

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
- [VSPackages](../extensibility/internals/vspackages.md)
