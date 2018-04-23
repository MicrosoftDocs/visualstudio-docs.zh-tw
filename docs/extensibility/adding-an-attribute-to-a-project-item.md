---
title: 將屬性加入專案項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d601a4cb3a7804520f0c9c95e746275e27db4bcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="adding-an-attribute-to-a-project-item"></a>將屬性加入專案項目
方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>取得並設定專案項目之屬性的值。 SetItemAttribute 建立的屬性已經存在，如果將它加入專案項目中繼資料。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>將屬性加入專案項目  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>若要將屬性加入專案項目  
  
-   下列程式碼會使用<xref:EnvDTE.DTE>automation 物件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>方法，將屬性加入專案項目。 專案項目 ID 被取自專案項目名稱"program.cs"。 屬性"MyAttribute"會加入至這個專案項目，且提供"MyValue"的值。  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [在 MSBuild 專案檔中保存資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)