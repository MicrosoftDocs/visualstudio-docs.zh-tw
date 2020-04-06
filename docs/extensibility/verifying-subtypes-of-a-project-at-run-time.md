---
title: 在執行時驗證項目的子類型 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698176"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>在執行時驗證項目的子型態
依賴於自定義專案子類型的 VSPackage 應包括用於查找該子類型的邏輯,以便在子類型不存在時,該子類型可以正常失敗。 下面的過程演示如何驗證是否存在指定的子類型。

### <a name="to-verify-the-presence-of-a-subtype"></a>驗證子類型是否存在

1. 通過將以下代碼添加到 VSPackage,從專案和解決方案<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件 中獲取專案層次結構作為物件。

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

2. 將層次結構強制轉換為<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>介面。

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 以呼叫 抓取的項目型態<xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>介面的清單 。

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 檢查清單以檢查指定子類型的 GUID。

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
- [專案子類型設計](../extensibility/internals/project-subtypes-design.md)
- [依專案子型態擴充的屬性和方法](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
