---
title: 在執行時間驗證專案的子類型 |Microsoft Docs
description: 瞭解如何讓您的 VSPackage 確認所相依的指定自訂專案子類型是否存在。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c52d3297ce4903cb8f8e7cb2f9ab5169d21ac94e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062599"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>在執行時間驗證專案的子類型
相依于自訂專案子類型的 VSPackage 應該包含尋找該子類型的邏輯，以便在子類型不存在時正常地失敗。 下列程式顯示如何確認指定的子類型是否存在。

### <a name="to-verify-the-presence-of-a-subtype"></a>確認子類型是否存在

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>將下列程式碼新增至您的 VSPackage，以將專案和方案物件中的專案階層取得為物件。

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

2. 將階層轉換為 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> 介面。

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 藉由叫用來取得專案類型 Guid 的清單 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> 。

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 檢查指定子類型的 GUID 清單。

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
- [專案子類型所擴充的屬性和方法](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
