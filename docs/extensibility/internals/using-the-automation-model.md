---
title: 使用 Automation 模型 |Microsoft Docs
description: 瞭解如何在連接到 automation 模型之後，取得 VSPackage 的屬性和方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e856153462819599124f3dce2e16c6de9f01cdfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883086"
---
# <a name="using-the-automation-model"></a>使用 Automation 模型
將 VSPackage 連接至自動化之後，您可以在物件上呼叫方法來取得屬性和方法 <xref:EnvDTE.DTEClass.GetObject%2A> <xref:EnvDTE._DTE> ，並傳遞代表您要抓取之物件的字串。

## <a name="obtaining-project-objects"></a>取得專案物件
 以下是兩個程式碼範例，示範 automation 取用者如何取得專案自動化物件。 如需如何取得 DTE 物件的詳細資訊，請參閱 [如何：取得 dte 和 DTE2 物件的參考](/previous-versions/68shb4dw(v=vs.140))。

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

 此時，您可以使用屬於特定 VSPackage 一部分的標準專案物件來下移階層模型。

 下列程式碼範例示範如何取得自訂物件，該物件為自訂專案類型的屬性。：

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 下列程式碼會在 [ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **工具**] 功能表上的 [環境 **一般**] 選項中，列出所有屬性的名稱：

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>另請參閱
- <xref:EnvDTE.DTEClass.GetObject%2A>