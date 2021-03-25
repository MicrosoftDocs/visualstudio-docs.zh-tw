---
title: 篩選嵌套專案的 AddItem 對話方塊 |Microsoft Docs
description: 瞭解如何藉由執行父專案的 IVsFilterAddProjectItemDlg 介面，在 Visual Studio 中篩選嵌套專案的 [AddItem] 對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59ae3c229ba359af0349ad93edc75e53c2cc3557
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069578"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>篩選嵌套專案的 AddItem 對話方塊
當您針對嵌套專案顯示 [ **AddItem** ] 對話方塊時，父專案可以控制要在對話方塊中顯示的專案。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面可讓您篩選將會出現在 **AddItem** 對話方塊中的節點。 當子專案顯示 [ **AddItem** ] 對話方塊時，父系可以執行 `IVsFilterAddProjectItemDlg` 介面並篩選以其他方式顯示在子專案中的專案。

 當專案依功能分組時，在特定的父專案下，您可以在 `IVsFilterAddProjectItemDlg` 使用者于嵌套專案的快捷方式功能表上選取 [ **加入專案專案** ] 時執行。 `IvsFilterAddProjectItemDlg displays`只執行該群組專屬的專案專案或檔案。 其他群組的專案專案會從對話方塊中篩選出來，即使它們儲存在相同的目錄中也一樣。

 當使用者開啟子系的 [ **AddItem** ] 對話方塊時，會呼叫父專案的介面實作為 `IVsFilterAddProjectItemDlg` 。

 `IVsFilterAddProjectItemDlg`介面也可以依類別來執行篩選。 如需詳細資訊，請參閱 [將專案加入至加入新專案對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 以及 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [嵌套專案](../../extensibility/internals/nesting-projects.md)
