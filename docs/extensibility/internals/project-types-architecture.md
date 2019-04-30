---
title: 專案類型架構 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3aee42e266e1082228c30ce56ac128e19ef6c576
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909456"
---
# <a name="project-types-architecture"></a>專案類型架構
本章節包含在專案類型架構的詳細的資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="in-this-section"></a>本節內容
- [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)

 列出專案類型可使用的服務，它必須實作的介面。

- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)

 描述專案類型都必須實作與選擇性可實作以提供其他功能的介面。

- [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)

 輸入可協助您決定當您必須在其中建立專案和時，您可以使用另一個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]擴充功能，例如 Vspackage 和編輯器，來達成相同的目標。

- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會使用階層和選取範圍內容來提供一致且簡化的使用者體驗。

## <a name="related-sections"></a>相關章節
- [專案子類型](../../extensibility/internals/project-subtypes.md)

 說明如何專案子類型可讓您自訂的專案系統的行為[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]。

- [專案類型](../../extensibility/internals/project-types.md)

 提供專案的概觀，做為基本建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 說明專案如何控制建置和編譯程式碼的其他主題會提供連結。