---
title: 使用自訂註冊屬性來註冊延伸模組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935780"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來登錄延伸模組
在某些情況下，您可能需要為您的延伸模組建立新的註冊屬性。 您可以使用註冊屬性來新增新的登錄機碼，或將新的值新增至現有的金鑰。 新的屬性必須衍生自 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，而且必須覆寫 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 和 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 方法。  
  
## <a name="creating-a-custom-attribute"></a>建立自訂屬性  
 下列程式碼顯示如何建立新的註冊屬性。  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>會在屬性類別上用來指定 (類別、方法等 ) 的程式元素、屬性所的專案，是否可以使用一次以上，以及是否可以繼承。  
  
### <a name="creating-a-registry-key"></a>建立登錄機碼  
 在下列程式碼中，自訂屬性會在要註冊的 VSPackage 機碼底下建立 **自訂** 子機碼。  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>在現有的登錄機碼下建立新的值  
 您可以將自訂值新增至現有的索引鍵。 下列程式碼示範如何將新值新增至 VSPackage 註冊金鑰。  
  
```  
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