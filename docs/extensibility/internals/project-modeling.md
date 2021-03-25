---
title: 專案模型 |Microsoft Docs
description: 瞭解為新的專案類型和專案自動化所遵循的路徑建立自動化所需的標準專案物件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 506606291996c94ff10514c6c57f83c6e1133862
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062820"
---
# <a name="project-modeling"></a>將專案模型化
為您的專案提供自動化的下一個步驟是執行標準專案物件： <xref:EnvDTE.Projects> 和集合、 `ProjectItems` `Project` 和 <xref:EnvDTE.ProjectItem> 物件，以及您的實作為唯一的其餘物件。 這些標準物件定義于 Dteinternal 檔中。 BscPrj 範例中提供標準物件的執行。 您可以使用這些類別作為模型來建立您自己的標準專案物件，這些物件與其他專案類型的專案物件並存。

 自動化取用者假設能夠呼叫 <xref:EnvDTE.Solution> (」 `<UniqueProjName>")` 和 <xref:EnvDTE.ProjectItems> (`n`) 其中 n 是取得方案中特定專案的索引編號。 進行此自動化呼叫會使環境在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> 適當的專案階層上呼叫，並傳遞 VSITEMID_ROOT 作為 ItemID 參數，並 VSHPROPID_ExtObject 為 VSHPROPID 參數。 `IVsHierarchy::GetProperty` 傳回 `IDispatch` automation 物件的指標，該物件提供您所執行的核心 `Project` 介面。

 以下是的語法 `IVsHierarchy::GetProperty` 。

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 專案可容納嵌套並使用集合來建立專案專案的群組。 階層看起來像這樣。

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 「嵌套」（ <xref:EnvDTE.ProjectItem> nested）表示物件可以 <xref:EnvDTE.ProjectItems> 同時集合，因為 `ProjectItems` 集合可以包含嵌套物件。 基本專案範例不會示範這種嵌套。 藉由執行此 `Project` 物件，您就可以參與類似樹狀結構，以反映整體 automation 模型的設計。

 專案自動化會遵循下圖中的路徑。

 ![Visual Studio 專案物件](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") 專案自動化

 如果您未執行 `Project` 物件，則環境仍會傳回 `Project` 只包含專案名稱的泛型物件。

## <a name="see-also"></a>另請參閱
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
