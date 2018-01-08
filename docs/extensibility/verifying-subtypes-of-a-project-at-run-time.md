---
title: "在執行階段驗證的專案子類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18049c034286c33247aec11aba77071daa93ef5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>在執行階段驗證專案的子類型
自訂專案子類型而定的 VSPackage 應該包含邏輯，以尋找子類型，讓它可以執行正常失敗子型別是否不存在。 下列程序示範如何確認存在指定的子類型。  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>若要確認有子型別  
  
1.  從專案和方案物件，以取得專案階層架構<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>VSPackage 中加入下列程式碼的物件。  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  轉換至階層<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>介面。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  取得叫用的專案類型的 Guid 清單<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>。  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  檢查指定的子類型的 GUID 清單。  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>請參閱  
 [專案子類型](../extensibility/internals/project-subtypes.md)   
 [專案子類型設計](../extensibility/internals/project-subtypes-design.md)   
 [專案子類型所擴充的屬性和方法](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)