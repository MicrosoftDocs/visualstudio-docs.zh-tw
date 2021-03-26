---
title: 管理設定選項 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中管理專案和解決方案設定，以控制您的專案的建立、封裝、部署和執行方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f773148f11a115ee82c8ee84a8d4668001908000
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095195"
---
# <a name="managing-configuration-options"></a>管理組態選項
當您建立新的專案類型時，您必須管理專案和方案設定，以決定如何建立、封裝、部署和執行您的專案。 下列主題討論專案和方案設定。

## <a name="in-this-section"></a>本節內容
- [概觀](../../extensibility/internals/configuration-options-overview.md)

 描述中的專案如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援多個設定。

- [屬性頁](../../extensibility/internals/property-pages.md)

 說明使用者可使用屬性頁來查看和變更專案設定相依屬性和獨立屬性。

- [解決方案設定](../../extensibility/internals/solution-configuration.md)

 提供儲存在解決方案設定中的資訊，以及解決方案設定如何指示 **Start** 和 **Build** 命令的行為。

- [專案組態物件](../../extensibility/internals/project-configuration-object.md)

 說明專案設定物件如何管理將設定資訊顯示到 UI 的方式。

- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)

 說明特定解決方案的解決方案設定清單如何由 [ **方案** 設定] 對話方塊管理。

- [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 定義部署的動作，而這兩種方式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援支援部署的專案。

- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)

 說明每個設定可支援的組建程式，以及可供使用輸出專案的介面和方法。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供專案的總覽，作為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 的基本組建區塊。 連結會提供給其他主題，以說明專案如何控制組建和編譯器代碼。
