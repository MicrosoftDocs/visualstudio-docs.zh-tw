---
title: 原始檔控制 VSPackage 架構 |Microsoft Docs
description: 瞭解原始檔控制套件的架構，這是 VSPackage，可提供 Visual Studio 為原始檔控制服務的功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4e9f19506c58f65f80900c08fe339c7478144546
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064224"
---
# <a name="source-control-vspackage-architecture"></a>原始檔控制 VSPackage 架構
原始檔控制封裝是使用 IDE 所提供之服務的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 在傳回時，原始檔控制封裝會以原始檔控制服務的形式提供其功能。 此外，原始檔控制封裝比原始檔控制外掛程式更具彈性，可將原始檔控制整合至其中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 原始檔控制外掛程式，它會執行嚴格合約所遵守的原始檔控制外掛程式 API。 例如，外掛程式無法取代 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (UI) 的預設使用者介面。 此外，原始檔控制外掛程式 API 不會讓外掛程式執行它自己的原始檔控制模型。 不過，原始檔控制封裝會克服這兩項限制。 原始檔控制套件可以完全掌控使用者的原始檔控制體驗 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 此外，原始檔控制封裝可以使用自己的原始檔控制模型和邏輯，也可以定義所有原始檔控制相關的使用者介面。

## <a name="source-control-package-components"></a>Source-Control 套件元件
 如架構圖所示，名為「 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制存根」的元件是一種整合原始檔控制套件的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 原始檔控制存根會處理下列工作。

- 提供原始檔控制套件註冊所需的通用 UI。

- 載入原始檔控制套件。

- 將原始檔控制封裝設定為主動/非使用中。

  原始檔控制存根會尋找原始檔控制封裝的作用中服務，並將所有傳入的服務呼叫從 IDE 路由到該套件。

  原始檔控制介面卡封裝是提供的特殊原始檔控制套件 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這個套件是根據原始檔控制外掛程式 API 來支援原始檔控制外掛程式的核心元件。 當原始檔控制外掛程式是使用中的外掛程式時，原始檔控制存根會將其事件傳送至原始檔控制介面卡封裝。 接著，原始檔控制介面卡封裝會使用原始檔控制外掛程式 API 與原始檔控制外掛程式進行通訊，也提供所有原始檔控制外掛程式通用的預設 UI。

  另一方面，如果原始檔控制封裝是使用中的封裝，則原始檔控制存根會使用 Source-Control 封裝介面，直接與封裝進行通訊 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。 原始檔控制套件負責裝載本身的原始檔控制 UI。

  ![Source Control Architecture 圖形](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  針對原始檔控制封裝，不 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供原始檔控制程式代碼或 API 來進行整合。 將此與 [建立原始](../../extensibility/internals/creating-a-source-control-plug-in.md) 檔控制外掛程式時所述的方法相比較，原始檔控制外掛程式必須執行一組固定的函式和回呼。

  如同任何 VSPackage，原始檔控制封裝是可使用建立的 COM 物件 `CoCreateInstance` 。 VSPackage 可讓您藉由實作為 IDE，讓它成為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 。 建立實例之後，VSPackage 會接收網站指標和 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 介面，提供 IDE 中可用服務和介面的 VSPackage 存取。

  撰寫以 VSPackage 為基礎的原始檔控制套件需要比撰寫原始檔控制外掛程式 API 型外掛程式更先進的程式設計專長。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
