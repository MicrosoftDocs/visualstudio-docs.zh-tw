---
title: 項目類型要點 |微軟文件
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
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706375"
---
# <a name="project-type-essentials"></a>專案類型的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包括語言(如或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)][!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]) 的多個項目類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]還允許您創建自己的項目類型。

 如果只想向 添加自定義命令、編輯器或工具[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]視窗 ,則可以在不創建新項目類型的情況下執行此操作。 如需詳細資訊，請參閱下列主題：

- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

- [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)

- [擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)

  同樣,如果要自定義提供的[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型的行為,則可以使用專案子類型執行此操作。 有關詳細資訊,請參閱[項目子類型](../../extensibility/internals/project-subtypes.md)。

  您必須建立以下語言的[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]語言的項目建立新的項目類型,[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]如果要支援以下一種或多項:

- 組建

- 部署

- 多種設定

- 原始檔控制

- 偵錯

- 解決方案資源管理員中的項目項目

- **開啟項目**'或 **'新增項目'** 對話框

- 專案嵌套

- 有關項目類型功能的詳細資訊,請參閱以下內容:

- 項目類型是 VSPackage 中實現[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預期介面 集的物件。 如果使用 C# 開發項目類型,託管包框架專案類將實現必要的介面,並允許您繼承該實現。 有關詳細資訊,請參閱[使用託管包框架實現項目類型 (C#)。](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- 對於C++開發人員來說,HierUtil 庫中的類的工作方式類似。 有關詳細資訊,請參閱[不在生成中:使用 HierUtil7 專案類實現專案類型 (C++)。](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)

- 專案類型可以支援生成到 .exe 或 .dll 程式集的典型原始程式碼檔以外的數據。 例如,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]資料庫專案包含對儲存在磁碟上的文本和查詢檔的引用,並將命令添加到**解決方案資源管理員**以針對資料庫執行腳本和查詢,但專案不支援生成行為。 有關詳細資訊,請參閱[開啟和儲存項目專案](../../extensibility/internals/opening-and-saving-project-items.md)。

- 項目類型根本不需要使用檔。 例如,專案類型可以將其所有數據存儲在資料庫中。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使專案類型完全控制它們如何持久化專案和專案項的數據。 有關詳細資訊,請參閱[項目類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

- 專案類型必須提供*專案工廠*,這是一個物件,每當被告知打開或創建基於該專案類型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的專案時,該物件都會創建專案類型的實例。 關於詳細資訊,請參閱[使用專案工廠建立項目實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。

- 項目類型必須為專案和專案項提供範本。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]當使用者創建新專案並將新專案添加到現有專案時,使用範本。 有關詳細資訊,請參閱[新增專案和專案項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

- 專案類型可以支援多種配置,如調試和發佈。 用戶可以使用您提供的屬性頁更改專案的不同配置。 關於詳細資訊,請參考[管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

## <a name="see-also"></a>另請參閱
- [部署專案類型](../../extensibility/internals/deploying-project-types.md)
