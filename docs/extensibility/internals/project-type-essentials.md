---
title: 專案類型基本 |Microsoft Docs
description: 瞭解何時必須建立專案類型，以及何時可以使用專案子類型來擴充現有的專案類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d55a4be044c44567f65e312d013ebdb61314ea00
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877789"
---
# <a name="project-type-essentials"></a>專案類型的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包含多種語言的專案類型，例如 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也可讓您建立自己的專案類型。

 如果您只想要將自訂命令、編輯器或工具視窗加入至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您可以在不建立新的專案類型的情況下進行。 如需詳細資訊，請參閱下列主題：

- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

- [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)

- [擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)

  同樣地，如果您想要自訂所提供 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案類型的行為，可以使用專案子類型來進行。 如需詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。

  如果專案是以以外的語言為基礎 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ，而且 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 您想要支援下列一或多個專案，就必須建立新的專案類型：

- Build

- 部署

- 多個設定

- 原始檔控制

- 偵錯

- 方案總管中的專案專案

- [ **開啟專案** ] 或 [ **新增專案** ] 對話方塊

- 專案嵌套

- 如需有關專案類型功能的詳細資訊，請參閱下列各項：

- 專案類型是 VSPackage 中的物件，可執行所預期的介面集 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 如果您使用 c # 開發專案類型，Managed 封裝架構專案類別會為您執行必要的介面，並讓您繼承該執行。 如需詳細資訊，請參閱 [使用 Managed Package Framework 來執行 c # )  (的專案類型 ](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)。

- 針對 c + + 開發人員，HierUtil 程式庫中的類別會以類似的方式運作。 如需詳細資訊，請參閱 [不在組建中：使用 HierUtil7 專案類別 (c + +) 執行專案類型 ](/previous-versions/bb166212(v=vs.100))。

- 專案類型可以支援建立為 .exe 或 .dll 元件的一般原始程式碼檔以外的資料。 例如， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 資料庫專案包含對儲存在磁片上之腳本和查詢檔案的參考，並將命令新增至 **方案總管** ，以針對資料庫執行腳本和查詢，但專案不支援組建行為。 如需詳細資訊，請參閱 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。

- 專案類型完全不需要使用檔案。 例如，專案類型可以將其所有資料儲存在資料庫中。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可讓專案類型完整控制其保存專案和專案專案資料的方式。 如需詳細資訊，請參閱 [專案類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

- 專案類型必須提供 *專案 factory*，也就是每當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 告知開啟或建立以該專案類型為基礎的專案時，會建立專案類型實例的物件。 如需詳細資訊，請參閱 [使用專案工廠建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。

- 專案類型必須提供專案和專案專案的範本。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 當使用者建立新專案，並將新的專案加入至現有的專案時，會使用這些範本。 如需詳細資訊，請參閱 [加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

- 專案類型可以支援多個設定，例如 Debug 和 Release。 使用者可以使用您提供的屬性頁，來變更專案的不同設定。 如需詳細資訊，請參閱 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

## <a name="see-also"></a>請參閱
- [部署專案類型](../../extensibility/internals/deploying-project-types.md)