---
title: 使用自動化模型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704225"
---
# <a name="using-the-automation-model"></a>使用 Automation 模型
將 VSPackage 連接到自動化後,可以<xref:EnvDTE.DTEClass.GetObject%2A><xref:EnvDTE._DTE>通過調用 物件上的方法來獲取屬性和方法,傳遞表示要檢索的物件的字串。

## <a name="obtaining-project-objects"></a>取得項目物件
 下面是兩個代碼示例,它們顯示了自動化消費者如何獲取專案自動化物件。 有關如何取得 DTE 物件的資訊,請參考[如何:取得對 DTE 與 DTE2 物件的參考](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)。

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

 此時,您可以使用作為特定 VSPackage 一部分的標準項目物件向下移動層次結構模型。

 以下代碼範例展示如何取得自訂項目類型的屬性的自訂物件:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 以下代碼列出了[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**「工具**」選單上的環境 **「一般」** 選項中的所有屬性的名稱:

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
