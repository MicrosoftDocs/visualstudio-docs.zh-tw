---
title: 在執行階段驗證的專案子類型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e77fa60687ecfebdae8555b516af678cf3966211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487689"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>在執行階段驗證專案的子類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[的專案中，於執行階段的驗證子](https://docs.microsoft.com/visualstudio/extensibility/verifying-subtypes-of-a-project-at-run-time)。  
  
自訂專案子類型而定的 VSPackage 應包含邏輯，以尋找子類型，讓它可以執行正常失敗的子類型是否不存在。 下列程序示範如何確認指定的子類型存在。  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>若要確認子型別存在  
  
1.  從專案和方案物件，做為取得專案階層架構<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>藉由將下列程式碼新增至 VSPackage 的物件。  
  
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
  
2.  轉換階層<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>介面。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  取得專案類型 Guid 的清單，藉由叫用<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [專案子類型](../extensibility/internals/project-subtypes.md)   
 [設計專案子類型](../extensibility/internals/project-subtypes-design.md)   
 [專案子類型所擴充的屬性和方法](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

