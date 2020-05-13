---
title: 項目類型體系結構 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706312"
---
# <a name="project-types-architecture"></a>專案類型架構
本節包含有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中 項目類型的體系結構的詳細資訊。

## <a name="in-this-section"></a>本節內容
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)

 列出項目類型可以使用的服務及其必須實現的介面。

- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)

 描述項目類型必須實現,可選地可以實現,以提供其他功能。

- [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)

 説明您確定何時必須創建項目類型,以及何時可以使用另一個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]擴充性功能(如 VSPackages 和編輯器)來實現相同的目標。

- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]層次結構和選擇上下文來提供一致和簡化的用戶體驗。

## <a name="related-sections"></a>相關章節
- [專案子類型](../../extensibility/internals/project-subtypes.md)

 說明專案子類型如何自定義[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]的專案系統的行為。

- [專案類型](../../extensibility/internals/project-types.md)

 提供專案概述,作為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成開發環境 (IDE) 的基本構建基塊。 連結指向其他主題,這些主題解釋了專案如何控制構建和編譯代碼。
