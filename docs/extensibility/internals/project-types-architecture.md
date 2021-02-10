---
title: 專案類型架構 |Microsoft Docs
description: 本文連結的文章包含 Visual Studio 中專案類型架構的詳細資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6c9463604cda8c26a53cb02802252dfe40d309b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970123"
---
# <a name="project-types-architecture"></a>專案類型架構
本章節包含中專案類型架構的詳細資訊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="in-this-section"></a>本節內容
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)

 列出專案類型可以取用的服務，以及它必須執行的介面。

- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)

 描述必須執行的介面專案類型，並選擇性地執行，以提供額外的功能。

- [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)

 協助您決定何時必須建立專案類型，以及當您可以使用其他擴充 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能（例如 vspackage 和編輯器）來達成相同的目標時。

- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

 描述如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用階層和選取內容來提供一致且簡化的使用者體驗。

## <a name="related-sections"></a>相關章節
- [專案子類型](../../extensibility/internals/project-subtypes.md)

 說明專案子類型如何讓您自訂和之專案系統的 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 行為 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 。

- [專案類型](../../extensibility/internals/project-types.md)

 提供專案的總覽，作為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 的基本組建區塊。 連結會提供給其他主題，以說明專案如何控制組建和編譯器代碼。
