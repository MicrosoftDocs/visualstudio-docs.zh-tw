---
title: 專案模型化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725565"
---
# <a name="project-modeling"></a>將專案模型化
為您的專案提供自動化的下一個步驟是執行標準專案物件： <xref:EnvDTE.Projects> 和 `ProjectItems` 集合;`Project` 和 <xref:EnvDTE.ProjectItem> 物件;以及您的實作為唯一的剩餘物件。 這些標準物件是在 Dteinternal 檔案中定義。 BscPrj 範例中提供標準物件的執行。 您可以使用這些類別作為模型，建立與其他專案類型的專案物件並存的標準專案物件。

 自動化取用者會假設能夠呼叫 <xref:EnvDTE.Solution> （"`<UniqueProjName>")` 和 <xref:EnvDTE.ProjectItems> （`n`），其中 n 是用來取得方案中特定專案的索引編號。 進行此自動化呼叫會使環境在適當的專案階層上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>，並將 VSITEMID_ROOT 當做 ItemID 參數傳遞，並將 VSHPROPID_ExtObject 當做 VSHPROPID 參數。 `IVsHierarchy::GetProperty` 會傳回 automation 物件的 `IDispatch` 指標，提供您已實作為核心 `Project` 介面。

 以下是 `IVsHierarchy::GetProperty` 的語法。

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`、

 `VSHPROPID` `propid`、

 `VARIANT` `*pvar`

 `);`

 專案會容納嵌套，並使用集合來建立專案專案的群組。 階層看起來像這樣。

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 [嵌套] 表示 <xref:EnvDTE.ProjectItem> 物件可以同時 <xref:EnvDTE.ProjectItems> 集合，因為 `ProjectItems` 集合可以包含該嵌套物件。 基本專案範例不會示範此嵌套。 藉由實作為 `Project` 物件，您就可以參與類似樹狀結構，其為整體自動化模型的設計。

 專案自動化會遵循下圖中的路徑。

 ![Visual Studio 專案物件](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")專案自動化

 如果您未執行 `Project` 物件，則環境仍然會傳回只包含專案名稱的泛型 `Project` 物件。

## <a name="see-also"></a>請參閱
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>