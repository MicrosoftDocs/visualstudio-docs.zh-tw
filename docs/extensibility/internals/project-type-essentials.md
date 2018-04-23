---
title: 專案類型 Essentials |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff6cc669d7df46acaa2cbcb129a6b13b7261d9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="project-type-essentials"></a>專案類型的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包含數種語言的專案類型，例如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也可讓您建立您自己的專案類型。  
  
 如果您只想要加入自訂命令、 編輯器或工具視窗， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您也不會建立新的專案類型。 如需詳細資訊，請參閱下列主題：  
  
-   [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 同樣地，如果您想要自訂所提供的行為[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型中，您可以使用專案子類型。 如需詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
 您必須建立新的專案類型的專案為基礎的語言以外[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]如果您想要支援的一或多個項目：  
  
-   組建  
  
-   部署  
  
-   多個組態  
  
-   原始檔控制  
  
-   偵錯  
  
-   在 [方案總管] 的專案項目  
  
-   **開啟專案**或**新專案**對話方塊  
  
-   專案的巢狀結構  
  
-   專案類型的功能的相關詳細資訊，請參閱下列各項：  
  
-   專案類型是在 VSPackage 中實作的介面集合的物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預期。 如果您使用 C# 來開發專案類型，Managed 封裝架構專案類別為您實作必要的介面，並可讓您可以繼承該實作。 如需詳細資訊，請參閱[實作專案型別 (C#) 使用 Managed Package Framework](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)。  
  
-   對於 c + + 開發人員，HierUtil 文件庫中的類別會在類似的方式。 如需詳細資訊，請參閱[不在組建中： 使用 HierUtil7 專案類別以實作專案類型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
-   專案類型都可以支援一般的原始程式碼檔建置為.exe 或.dll 的組件以外的資料。 例如，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包含指令碼和查詢的檔案儲存在磁碟上的參考資料庫專案，並將命令加入至**方案總管 中**執行指令碼和查詢資料庫，但專案不支援建置行為。 如需詳細資訊，請參閱[開啟和儲存的專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
-   若要使用的檔案完全沒有專案類型。 例如，專案類型無法儲存在資料庫的所有資料。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可讓專案類型完全控制它們將專案和專案項目資料的保存。 如需詳細資訊，請參閱[專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
-   必須提供專案類型*專案 factory*，這是建立專案的執行個體的物件時輸入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]告知開啟或建立該專案類型為基礎的專案。 如需詳細資訊，請參閱[建立專案執行個體所使用的專案 Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
-   專案類型都必須提供專案和專案項目範本。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 當使用者建立新的專案，並將新項目加入至現有的專案，請使用範本。 如需詳細資訊，請參閱[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
-   專案類型可支援多個組態，例如偵錯和發行。 使用者可以使用您提供的屬性頁變更專案的不同的組態。 如需詳細資訊，請參閱[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署專案類型](../../extensibility/internals/deploying-project-types.md)