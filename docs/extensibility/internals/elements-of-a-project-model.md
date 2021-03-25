---
title: 專案模型的元素 |Microsoft Docs
description: 深入瞭解專案模型的專案，以及 Visual Studio 中所有專案的介面和執行方式如何共用基本結構。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85b31996a7a0636f136e43531e69fe25c6d87d8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061286"
---
# <a name="elements-of-a-project-model"></a>專案模型的元素
中所有專案的介面和實 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 作為共用基本結構：專案類型的專案模型。 在您要開發的 VSPackage 專案模型中，您會建立符合設計決策的物件，並與 IDE 所提供的全域功能一起運作。 您可以控制專案專案的保存方式，例如，您無法控制必須保存檔案的通知。 當使用者將焦點放在開啟的專案專案，並在功能表列上的 [檔案 **] 功能表上選擇 [** **儲存**] 時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您的專案類型程式碼必須從 IDE 攔截命令、保存檔案，然後將通知傳送回 ide，表示檔案已不再變更。

 您的 VSPackage 會透過提供 IDE 介面存取權的服務，與 IDE 互動。 例如，透過特定的服務，您可以監視和路由傳送命令，並提供在專案中所做選擇的內容資訊。 VSPackage 所需的所有全域識別碼E 功能都是由服務所提供。 如需服務的詳細資訊，請參閱 [如何：取得服務](../../extensibility/how-to-get-a-service.md)。

 其他實行考慮：

- 單一專案模型可以包含一個以上的專案類型。

- 專案類型和「附隨」專案 factory 會與 Guid 分開註冊。

- 當使用者透過 UI 建立新專案時，每個專案都必須具有範本檔案或 wizard，才能初始化新的專案檔 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 例如， [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 範本會初始化最終變成 vcproj 檔案的內容。

  下圖顯示組成一般專案執行的主要介面、服務和物件。 您可以使用應用程式協助程式 `HierUtil7` 來建立基礎物件和其他程式設計的程式設計。 如需應用程式協助程式的詳細資訊 `HierUtil7` ，請參閱 [使用 HierUtil7 專案類別來執行 c + +)  (的專案類型 ](/previous-versions/bb166212(v=vs.100))。

  ![Visual Studio 專案模型圖形](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") 專案模型

  如需上圖中所列介面和服務的詳細資訊，以及圖表中未包含的其他選用介面，請參閱 [專案模型核心元件](../../extensibility/internals/project-model-core-components.md)。

  專案可支援命令，因此必須 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 透過命令內容 guid 來執行介面，以參與命令路由。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [使用 HierUtil7 專案類別來執行 c + + (的專案類型) ](/previous-versions/bb166212(v=vs.100))
- [專案模型核心元件](../../extensibility/internals/project-model-core-components.md)
- [使用 project factory 建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [How to：取得服務](../../extensibility/how-to-get-a-service.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)