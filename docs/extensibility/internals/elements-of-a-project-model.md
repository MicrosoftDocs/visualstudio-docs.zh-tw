---
title: 專案模型的元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708529"
---
# <a name="elements-of-a-project-model"></a>專案模型的元素
中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所有專案的介面和實現共用一個基本結構:專案類型的專案模型。 在專案模型中(即您正在開發的 VSPackage)中,您將創建符合設計決策的物件,並與 IDE 提供的全域功能協同工作。 例如,儘管控制專案項的保留方式,但不控制必須保留檔的通知。 當使用者將焦點放在打開的專案項上並選擇 **「保存在**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**選單欄上的檔案**」功能表上時,專案類型代碼必須攔截 IDE 的命令,保留檔,並將檔發送回 IDE,通知檔不再更改。

 您的 VS 套件透過提供對 IDE 介面的存取的服務與 IDE 進行互動。 例如,通過特定服務,您可以監視和路由命令,併為專案中所做的選擇提供上下文資訊。 VSPackage 所需的所有全球 IDE 功能均由服務提供。 有關服務的詳細資訊,請參閱[如何:獲取服務](../../extensibility/how-to-get-a-service.md)。

 其他實現注意事項:

- 單個專案模型可以包含多個項目類型。

- 項目類型和相應的項目工廠在 GUID 中獨立註冊。

- 當使用者透過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI 創建新專案時,每個專案都必須具有範本檔或嚮導來初始化新專案檔。 例如,[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]模板初始化最終成為 .vcproj 檔的內容。

  下圖顯示了構成典型項目實現的主要介面、服務和物件。 您可以使用應用程式幫助器`HierUtil7`,創建基礎物件和其他程式設計樣板。 有關`HierUtil7`應用程式協助程式的詳細資訊,請參閱[使用 HierUtil7 專案類別來實現項目類型 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)。

  ![視覺化工作室專案模型圖形](../../extensibility/internals/media/vsprojectmodel.gif "vs 專案模型")專案模型

  有關上圖中列出的介面和服務以及關係圖中未包括的其他可選介面的詳細資訊,請參閱[Project 模型核心元件](../../extensibility/internals/project-model-core-components.md)。

  專案可以支援命令,因此必須實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面才能通過命令上下文 GUID 參與命令路由。

## <a name="see-also"></a>另請參閱
- [檢查表:建立新的項目型態](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用 HierUtil7 專案類別 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [專案模型核心元件](../../extensibility/internals/project-model-core-components.md)
- [使用項目工廠建立項目實體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [如何:取得服務](../../extensibility/how-to-get-a-service.md)
- [建立項目型態](../../extensibility/internals/creating-project-types.md)
