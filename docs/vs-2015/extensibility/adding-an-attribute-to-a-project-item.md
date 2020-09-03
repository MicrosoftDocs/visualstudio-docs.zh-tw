---
title: 將屬性加入至專案專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184824"
---
# <a name="adding-an-attribute-to-a-project-item"></a>將屬性新增至專案項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> 以及 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 取得和設定專案專案的屬性值。 SetItemAttribute 會建立屬性（如果它不存在），並將它加入至專案專案中繼資料。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>將屬性加入至專案專案  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>將屬性加入至專案專案  
  
- 下列程式碼會使用 <xref:EnvDTE.DTE> automation 物件和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 方法，將屬性加入至專案專案。 專案專案識別碼是從專案專案名稱 "program.cs" 取得的。 屬性 "MyAttribute" 會新增至這個專案專案，並指定值 "MyValue"。  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [在 MSBuild 專案檔中保存資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
