---
title: 擴充 SharePoint 專案系統 |Microsoft Docs
description: 擴充 SharePoint 專案系統。 瞭解如何延伸 SharePoint 專案系統。 瞭解一般開發工作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5a81fef67cc6816f16a074494005a61d647abeab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889677"
---
# <a name="extend-the-sharepoint-project-system"></a>擴充 SharePoint 專案系統
  您可以使用 Visual Studio 中的一組專案範本和專案範本來建立 SharePoint 方案。 這些範本符合許多開發案例的需求，但您可能會發現它們無法提供您所需的功能。 在這些情況下，您可以擴充 SharePoint 專案系統。

## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint 專案系統總覽
 SharePoint 專案系統是以 *sharepoint 專案專案* 的基本元件為基礎。 SharePoint 專案專案代表單一 SharePoint 自訂，例如清單定義、網頁元件或內容類型。

 SharePoint 專案是包含一或多個 SharePoint 專案專案的 Visual Studio 專案。 SharePoint 專案也包含其他元件，以定義如何將專案專案分組為部署的功能和套件。

 如需有關 SharePoint 專案專案和 SharePoint 專案內容的詳細資訊，請參閱 [建立 sharepoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

## <a name="how-to-extend-the-sharepoint-project-system"></a>如何延伸 SharePoint 專案系統
 您可以利用下列方式來擴充 SharePoint 專案系統：

- 定義您自己的 SharePoint 專案專案類型，並將其與 Visual Studio 中的新專案範本或專案範本產生關聯。 例如，您可以定義用來建立自訂動作或欄位的 SharePoint 專案專案類型。 如需詳細資訊，請參閱 [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。

- 擴充已安裝在 Visual Studio 中的 SharePoint 專案專案類型。 例如，您可以將快捷方式功能表項目加入至 **方案總管** 中的專案專案，並在開發人員選擇功能表項目時自訂專案專案。 如需詳細資訊，請參閱 [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)。

- 擴充 SharePoint 專案。 例如，您可以新增事件處理常式，以便在 SharePoint 專案中加入或移除專案時執行特定的工作。 如需詳細資訊，請參閱 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)。

- 擴充 SharePoint 專案專案和 SharePoint 專案的封裝和部署行為。 例如，您可以建立自己的部署步驟，以在部署或撤銷專案時執行，也可以在 Visual Studio 執行某些部署步驟時，執行額外的自訂工作。 如需詳細資訊，請參閱 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。

## <a name="common-development-tasks"></a>一般開發工作
 您可以在 SharePoint 專案系統的延伸模組中執行下列一般工作：

- 使用專案專案和數種不同類型的專案檔來儲存自訂字串資料。 如需詳細資訊，請參閱 [在 SharePoint 專案系統的延伸中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

- 將 SharePoint 專案系統中的物件轉換為 Visual Studio automation 物件模型或整合物件模型中的對應物件，反之亦然。 如需詳細資訊，請參閱 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間的 Conver](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。

## <a name="see-also"></a>另請參閱
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [將資料儲存在 SharePoint 專案系統的延伸模組中](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [在 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint 工具擴充功能的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
