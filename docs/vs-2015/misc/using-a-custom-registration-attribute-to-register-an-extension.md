---
title: 使用自訂註冊屬性來登錄延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: douge
ms.openlocfilehash: 251c31efcbb8a72efac51f246e644a30a79ed999
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279834"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>使用自訂註冊屬性來登錄延伸模組
在某些情況下，您可能需要建立新的註冊屬性，您的擴充功能。 若要加入新的登錄機碼，或將新的值加入至現有的索引鍵，您可以使用註冊屬性。 新的屬性必須衍生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，而且它必須覆寫<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
## <a name="creating-a-custom-attribute"></a>建立自訂屬性  
 下列程式碼示範如何建立新的註冊屬性。  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute>屬性類別上用來指定與屬性，是否就可以使用一次以上，以及是否可繼承的程式元素 （類別、 方法等）。  
  
### <a name="creating-a-registry-key"></a>建立登錄機碼  
 下列程式碼，建立自訂的屬性**自訂**vspackage 所登錄機碼下的子機碼。  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>建立現有的登錄機碼下的新值  
 您可以新增自訂值到現有的金鑰。 下列程式碼示範如何將新的值新增至 VSPackage 註冊金鑰。  
  
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