---
title: 加入專案和專案項目範本 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38ab7a0a14c5a4e832aec330852546b64a41fd0c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315853"
---
# <a name="add-project-and-project-item-templates"></a>將專案和專案項目範本
當您建立您自己的專案類型時，您必須提供支援加入新的專案和專案項目使用標準[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 對話方塊。 下列主題討論不同的技術，讓您新增的專案和專案項目。

## <a name="in-this-section"></a>本節內容
- [專案內容](../../extensibility/internals/project-context.md)

 說明專案提供大部分的什麼瓿在環境中的內容資訊。

- [專案優先順序](../../extensibility/internals/project-priority.md)

 說明專案項目通常是一個專案的成員，才能避免模稜兩可，哪些專案用來開啟項目。

- [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)

 提供專案扮演判斷哪一個編輯器，開啟專案項目時所要使用的兩種可用來在專案和角色中開啟檔案的編輯器類型的資訊。

- [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)

 說明發生的狀況時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建立專案。

- [將項目新增至 [加入新項目] 對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 說明的程序新增項目**加入新項目** 對話方塊。

- [將目錄新增至方塊中的 [新增專案] 對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 提供註冊新的目錄，其中包含 VSPackage 所提供的自訂範本的範例。

- [將目錄新增至 [加入新項目] 對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 提供的範例註冊一組新的目錄**加入新項目** 對話方塊。

- [IDE 定義的命令，來擴充專案系統](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 列出不同類型的擴充專案系統使用的命令項目。

- [Catid 通常用來擴充專案的物件](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 列出可用來擴充的物件 Catid [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案系統。

## <a name="related-sections"></a>相關章節
- [如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)

 提供逐步指示，開啟本質繫結至特定的編輯器專案項目。

- [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)

 提供逐步指示，開啟標準編輯器。

- [專案子類型](../../extensibility/internals/project-subtypes.md)

 提供專案子類型概念性主題的連結。 專案子類型會延伸現有[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。

- [專案類型](../../extensibility/internals/project-types.md)

 提供額外的主題提供有關如何設計新的專案類型的資訊連結。