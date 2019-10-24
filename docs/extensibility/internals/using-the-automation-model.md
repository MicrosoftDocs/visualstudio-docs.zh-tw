---
title: 使用 Automation 模型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722086"
---
# <a name="using-the-automation-model"></a>使用 Automation 模型
將 VSPackage 連接至自動化之後，您可以在 <xref:EnvDTE._DTE> 物件上呼叫 <xref:EnvDTE.DTEClass.GetObject%2A> 方法來取得屬性和方法，傳遞代表您要抓取之物件的字串。

## <a name="obtaining-project-objects"></a>取得專案物件
 以下是兩個程式碼範例，示範自動化取用者如何取得專案自動化物件。 如需如何取得 DTE 物件的詳細資訊，請參閱[如何：取得 dte 和 DTE2 物件的參考](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)。

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 此時，您可以使用屬於特定 VSPackage 之一部分的標準專案物件，在階層模型中向下移動。

 下列程式碼範例示範如何取得做為自訂專案類型之屬性的自訂物件：

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 下列程式碼會列出 [**工具**] 功能表上 [[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境] **[一般**] 選項中所有屬性的名稱：

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>請參閱
- <xref:EnvDTE.DTEClass.GetObject%2A>