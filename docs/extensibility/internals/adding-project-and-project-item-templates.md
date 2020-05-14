---
title: 新增項目和項目項目樣本 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710200"
---
# <a name="add-project-and-project-item-templates"></a>新增項目和項目項目樣本
建立自己的項目類型時,必須使用標準[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 對話方塊支援添加新專案和專案項目。 以下主題討論添加專案和專案項的不同技術。

## <a name="in-this-section"></a>本節內容
- [專案內容](../../extensibility/internals/project-context.md)

 說明專案提供了環境中發生的情況的大部分上下文資訊。

- [專案優先權](../../extensibility/internals/project-priority.md)

 說明專案項通常是一個專案的成員,以説明避免有關用於打開專案的專案的歧義。

- [雜項檔案專案](../../extensibility/internals/miscellaneous-files-project.md)

 提供有關可用於在專案中打開檔的兩種類型的編輯器以及專案在確定打開專案項時要使用的編輯器所扮演的角色的資訊。

- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)

 解釋創建[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案時發生的情況。

- [新增項目新增項目新增項目對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 解釋向「**添加新專案」** 對話方塊中添加項的過程。

- [將目錄新增到「新項目」對話框](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 提供了註冊包含 VSPackage 提供的自定義範本的新目錄的範例。

- [新增項目新增的項目中](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 提供了為 **「添加新專案」** 對話方塊註冊一組新目錄的範例。

- [擴充項目系統的 IDE 定義指令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 列出用於擴展項目系統的不同類型的命令項。

- [通常用於延伸項目的物件的 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 列出用於擴[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]充的[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]物件的 CATID 和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案系統。

## <a name="related-sections"></a>相關章節
- [如何:開啟特定於項目的編輯器](../../extensibility/how-to-open-project-specific-editors.md)

 提供用於打開與專案的特定編輯器綁定的項的分步說明。

- [如何:開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)

 提供打開標準編輯器的分步說明。

- [專案子類型](../../extensibility/internals/project-subtypes.md)

 提供指向專案子類型概念主題的連結。 專案子類型擴展現有[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。

- [專案類型](../../extensibility/internals/project-types.md)

 提供指向其他主題的連結,這些主題提供有關如何設計新項目類型的資訊。
