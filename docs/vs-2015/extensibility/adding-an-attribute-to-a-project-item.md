---
title: 將屬性加入至專案項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6854b4895ff03d575a3d26fad0e1117debf932f1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302688"
---
# <a name="adding-an-attribute-to-a-project-item"></a>將屬性新增至專案項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>取得和設定的專案項目屬性的值。 SetItemAttribute 建立屬性如果已經存在，將它新增至專案項目中繼資料。  
  
## <a name="adding-an-attribute-to-a-project-item"></a>將屬性加入至專案項目  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>若要將屬性加入專案項目  
  
-   下列程式碼會使用<xref:EnvDTE.DTE>automation 物件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>方法，將屬性加入至專案項目。 專案項目 ID 被取自專案項目名稱"program.cs"。 屬性"MyAttribute"會加入至這個專案項目，而且 「 MyValue"的值。  
  
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

