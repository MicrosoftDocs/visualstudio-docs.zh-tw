---
title: 原始檔控制整合總覽 |Microsoft Docs
description: 瞭解將原始檔控制整合至 Visual Studio 的兩種方式之間的差異：原始檔控制外掛程式和 VSPackage。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9feacd8e051b47b1fec6c3d3ad08e34e591fc57c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064302"
---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節將比較兩種整合至 Visual Studio 原始檔控制的方式;原始檔控制外掛程式和提供原始檔控制解決方案的 VSPackage，並強調新的原始檔控制功能。 Visual Studio 可讓您在原始檔控制 Vspackage 和原始檔控制外掛程式，以及自動以方案為基礎的切換之間進行手動切換。

## <a name="source-control-integration"></a>原始檔控制整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合選項。 在所有版本的中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您仍然可以根據原始檔控制外掛程式 API 來整合外掛程式， (先前也稱為 MSSCCI API) ，可在使用 Visual Studio 原始檔控制使用者介面 (UI) 時提供基本的原始檔控制功能。 另一方面，原始檔控制 VSPackage 提供新的深層整合 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 路徑，適用于原始檔控制整合，在其原始檔控制模型中要求高階的複雜和自主性。

 ![原始檔控制總覽](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 所有版本的 Visual Studio 都支援原始檔控制外掛程式 API 規格1.2 版作為整合路徑。 原始檔控制外掛程式可讓您撰寫 DLL，以執行原始檔控制整合和註冊的原始檔控制外掛程式 API 函式，如 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)所述。 使用這個方法時，整合式開發環境 (IDE) 會使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 對話方塊的 UI，例如簽入、簽出、工具/選項屬性頁、工具列和原始檔控制圖像。 嚴格遵循原始檔控制外掛程式 API，可讓您輕鬆地整合到 Visual Studio，並讓使用者有無問題的體驗。 這表示原始檔控制外掛程式必須執行 API 中詳述的大部分函式和回呼。

 若要使用原始檔控制外掛程式 API 來執行原始檔控制外掛程式，請遵循下列步驟：

1. 建立可執行 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)中所指定之函式的 DLL。

2. 藉由依照 [如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)) 所述，建立適當的登錄 (專案以註冊 DLL。

3. 當原始檔控制介面卡封裝的提示 (透過原始檔控制外掛程式處理原始檔控制功能的 Visual Studio 元件時，請建立協助程式 UI 並顯示) 

   為了回應原始檔控制命令，Visual Studio IDE 會顯示基本作業的標準 UI，然後透過原始檔控制外掛程式 API 中所定義的函式，將資訊傳遞至原始檔控制外掛程式。 若為 advanced options，可以呼叫原始檔控制外掛程式，以呈現自己的 UI，例如，流覽原始檔控制的專案。 這表示在處理原始檔控制時，使用者可能會看到兩種可能不同的 UI 樣式： Visual Studio 顯示的 UI，以及原始檔控制外掛程式所呈現的 UI。 這在 advanced source control 作業中最為明顯。

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>執行原始檔控制外掛程式的缺點

- 針對先進的功能，使用者可能會看到兩種不同的介面樣式，導致可能的混淆。

- 原始檔控制外掛程式受限於原始檔控制外掛程式 API 所隱含的原始檔控制模型。

- 原始檔控制外掛程式 API 對某些原始檔控制案例而言可能太嚴格。

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>執行原始檔控制外掛程式的優點

- Visual Studio 提供所有基本原始檔控制作業的所有 UI，讓原始檔控制外掛程式不需要執行可能複雜的 UI。

- 由於是嚴格的 API，因此，原始檔控制外掛程式可以輕鬆地與外部原始檔控制程式互動，以提供更廣泛的功能;Visual Studio 並不在意如何完成原始檔控制功能，只是根據原始檔控制外掛程式 API 來完成。

- 比起原始檔控制 VSPackage，您可以更輕鬆地執行原始檔控制外掛程式。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 允許與 Visual Studio 的深度整合，完全掌控原始檔控制功能，並完全取代 Visual Studio 提供的原始檔控制使用者介面。 原始檔控制 VSPackage 已向 Visual Studio 註冊，並提供原始檔控制功能。 雖然有數個原始檔控制 Vspackage 可以向 Visual Studio 登錄，但其中一次只能有一個作用中。 原始檔控制 VSPackage 具有原始檔控制功能的完整控制權，並可在使用中時 Visual Studio 的外觀。 可能在系統中註冊的其他所有原始檔控制 Vspackage 都處於非使用中狀態，而且完全不會顯示任何 UI。

 執行原始檔控制 VSPackage 需要「全部」或「無」策略。 原始檔控制 VSPackage 的建立者必須投入大量的精力來執行一些原始檔控制介面和新的 UI 元素， (對話方塊、功能表和工具列) ，以涵蓋整個原始檔控制功能。 如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) 。

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>執行原始檔控制 VSPackage 的缺點

- VSPackage 必須執行一些複雜的介面，才能成功地與 Visual Studio 整合。

- VSPackage 必須提供原始檔控制所需的所有 UI;Visual Studio 不會在此區域中提供任何協助。

- 原始檔控制 VSPackage 會瞭若指掌系結至 Visual Studio，且無法與獨立程式一起運作，因此功能無法輕易地與原始檔控制程式的外部版本共用。

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>執行原始檔控制 VSPackage 的優點

- 由於 VSPackage 具有原始檔控制 UI 和功能的完整控制權，因此使用者會看到適用于原始檔控制的無縫介面。

- VSPackage 不限於特定的原始檔控制模型。

## <a name="see-also"></a>另請參閱
- [原始檔控制](../../extensibility/internals/source-control.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [原始檔控制的新功能](../../extensibility/internals/what-s-new-in-source-control.md)
