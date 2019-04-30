---
title: 專案模型的項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e14086ea395ffe65a52f47d0bfaa320fb19bc8f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910063"
---
# <a name="elements-of-a-project-model"></a>專案模型的項目
介面和實作中的所有專案的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]共用基本結構： 您的專案類型的專案模型。 在您專案的模型，也就是您正在開發的 VSPackage，您可以建立符合您的設計決策，且 IDE 所提供的通用功能搭配運作的物件。 雖然您可以控制如何保存專案項目，例如，您無法控制通知檔案必須 persisted。 當使用者將焦點放在開啟的專案項目，並選擇**儲存**上**檔案**功能表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能表列中，您的專案型別程式碼必須攔截從 IDE 命令、 保留檔案，並將通知傳送回 IDE 會不會再變更的檔案。

 VSPackage 會提供 IDE 介面的存取權的服務透過 IDE 與互動。 比方說，透過特定的服務，您監視和路由命令，並提供選取之項目的專案中的內容資訊。 Vspackage 所需所有通用的 IDE 功能是由服務提供。 如需有關服務的詳細資訊，請參閱[How to:取得服務](../../extensibility/how-to-get-a-service.md)。

 其他實作考量：

- 單一專案模型可以包含多個專案類型。

- 專案類型以及語音應答專案處理站會向獨立 Guid。

- 每個專案都必須有範本檔案或初始化新的專案檔案，當使用者建立新的專案，透過精靈[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI。 比方說，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]範本初始化項目最後會變成.vcproj 檔案。

  下圖顯示主要的介面、 服務和 compose 的典型專案中實作的物件。 您可以使用應用程式協助程式`HierUtil7`，以建立基礎物件和其他程式設計的重複使用。 如需詳細資訊`HierUtil7`應用程式的協助程式，請參閱 <<c2> [ 使用 HierUtil7 專案類別以實作專案類型 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)。</c2>

  ![Visual Studio 專案模型圖形](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")專案模型

  如需有關介面和服務列在上圖中，與其他選擇性介面不包含在圖表的詳細資訊，請參閱[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)。

  專案可以支援的命令，並因此必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面來參與命令路由，透過命令內容的 Guid。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用 HierUtil7 專案類別來實作專案類型 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)
- [使用 project factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [如何：取得服務](../../extensibility/how-to-get-a-service.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)
