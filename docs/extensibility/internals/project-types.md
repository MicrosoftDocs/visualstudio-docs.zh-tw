---
title: 專案類型 |Microsoft Docs
description: 'Visual Studio 包含多種語言的專案類型，例如 Visual c # 和 Visual Basic。 Visual Studio 也可讓您建立自己的專案類型。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, adding
- projects [Visual Studio SDK], adding new types
ms.assetid: 263a084f-f97a-4e09-add7-f0e8a6a27daf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05db128709fcd0e99b3d0a3a6b26acbc372212c7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064265"
---
# <a name="project-types"></a>專案類型
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包含多種語言的專案類型，例如 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也可讓您建立自己的專案類型。

## <a name="in-this-section"></a>本節內容
- [基本功能](../../extensibility/internals/project-type-essentials.md)

 提供開始使用專案類型時必須具備的重要資訊。

- [建立專案類型](../../extensibility/internals/creating-project-types.md)

 討論專案類型的設計。

- [將命令加入至方案總管工具列](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)

 詳細說明將按鈕新增至方案總管工具列時必須遵循的步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  。

- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

 討論如何將範本加入至您的專案類型，讓使用者可以根據模式來建立新的專案和專案專案。

- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)

 提供有關如何管理您的專案類型支援之專案的資訊。

- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)

 討論您的專案類型如何支援 Debug 和 Release 等設定選項，以控制專案的建立、調試等等。

- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)

 提供有關如何將原始檔控制系統的支援新增至您的專案類型的資訊。

- [巢狀專案](../../extensibility/internals/nesting-projects.md)

 說明專案類型如何支援 *嵌套*，讓專案可以在 **方案總管** 中群組在一起。

- [升級專案](../../extensibility/internals/upgrading-projects.md)

 描述您的專案類型如何參與升級嚮導，以升級舊版的專案檔 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [架構](../../extensibility/internals/project-types-architecture.md)

 提供有關專案類型的詳細技術資訊。

## <a name="related-sections"></a>相關章節
- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

 概要說明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 如何將專案顯示為階層。

- [專案子類型](../../extensibility/internals/project-subtypes.md)

 提供專案子類型主題的連結。 專案子類型可延伸大部分類型的專案類型，包括您自己的專案類型。

- [專案](../../extensibility/internals/projects.md)

 說明如何擴充 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案系統。
