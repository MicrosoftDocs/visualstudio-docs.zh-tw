---
title: 在執行階段驗證的專案子類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 033f2971d0b8acb0390765f240a86a5ff543c353
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310693"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>在執行階段驗證專案的子類型
自訂專案子類型而定的 VSPackage 應包含邏輯，以尋找子類型，讓它可以執行正常失敗的子類型是否不存在。 下列程序示範如何確認指定的子類型存在。

### <a name="to-verify-the-presence-of-a-subtype"></a>若要確認子型別存在

1. 從專案和方案物件，做為取得專案階層架構<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>藉由將下列程式碼新增至 VSPackage 的物件。

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. 轉換階層<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>介面。

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 取得專案類型 Guid 的清單，藉由叫用<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>。

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 檢查指定的子類型的 GUID 清單。

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>另請參閱
- [專案子類型](../extensibility/internals/project-subtypes.md)
- [設計專案子類型](../extensibility/internals/project-subtypes-design.md)
- [屬性和專案子類型所擴充的方法](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)