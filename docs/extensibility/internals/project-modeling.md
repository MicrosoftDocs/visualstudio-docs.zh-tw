---
title: 專案建模 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706546"
---
# <a name="project-modeling"></a>將專案模型化
為專案提供自動化的下一步是實現標準專案物件:<xref:EnvDTE.Projects>`ProjectItems`和集合;`Project`和<xref:EnvDTE.ProjectItem>物件;以及實現所特有的其餘物件。 這些標準物件在 Dtein.h 檔中定義。 BscPrj 範例提供了標準物件的實現。 可以將這些類用作模型,以創建與來自其他項目類型的專案物件並排站在一起的標準項目物件。

 自動化消費者<xref:EnvDTE.Solution>假定能夠調用`<UniqueProjName>")`(" 和<xref:EnvDTE.ProjectItems>)`n`,其中 n 是獲取解決方案中特定專案的索引號。 進行此自動化調用會導致環境調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>相應的專案層次結構,將VSITEMID_ROOT作為 ItemID 參數傳遞,並將VSHPROPID_ExtObject作為 VSHPROPID 參數。 `IVsHierarchy::GetProperty`返回指向`IDispatch`提供`Project`核心介面的自動化物件的指標,該介面已實現。

 下面是`IVsHierarchy::GetProperty`的語法。

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 專案容納嵌套並使用集合創建項目項組。 層次結構如下所示。

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 嵌套意味著<xref:EnvDTE.ProjectItem>可以<xref:EnvDTE.ProjectItems>同時 收集物件`ProjectItems`,因為集合可以包含嵌套物件。 基本專案示例不演示此嵌套。 通過實現物件`Project`,您可以參與整個自動化模型設計的特徵樹狀結構。

 專案自動化遵循下圖中的路徑。

 ![視覺化工作室項目物件](../../extensibility/internals/media/projectobjects.gif "專案物件")專案自動化

 如果不實現`Project`物件,環境仍將返回僅包含專案名稱的泛`Project`型 物件。

## <a name="see-also"></a>另請參閱
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
