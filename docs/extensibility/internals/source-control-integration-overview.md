---
title: 原始檔控制整合總覽 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f714bfdfc94cb9481071becf1cdc95f5259e975
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723541"
---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節將比較兩種整合到 Visual Studio 原始檔控制的方式;原始檔控制外掛程式，以及提供原始檔控制方案的 VSPackage，並強調新的原始檔控制功能。 Visual Studio 允許在原始檔控制 Vspackage 和原始檔控制外掛程式之間手動切換，以及自動以解決方案為基礎的切換。

## <a name="source-control-integration"></a>原始檔控制整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合選項。 在所有版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中，您仍然可以根據原始檔控制外掛程式 API （先前也稱為 MSSCCI API）來整合外掛程式，以在使用 Visual Studio 原始檔控制使用者介面（UI）時提供基本的原始檔控制功能。 另一方面，原始檔控制 VSPackage 提供了一種新的深度整合 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 路徑，適用于原始檔控制整合，在其原始檔控制模型中要求高層級的複雜和獨立性。

 ![原始檔控制總覽](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 所有版本的 Visual Studio 都支援原始檔控制外掛程式 API 規格1.2 版做為整合路徑。 原始檔控制外掛程式實施者會針對原始檔控制外掛程式 API 函式（如[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)中所述），撰寫一個 DLL 來執行原始檔控制外掛程式 API 函式。 在這種方法中，整合式開發環境（IDE）會使用對話方塊的 [[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]] UI，例如 [簽入]、[簽出]、[工具]/[選項] 屬性頁、工具列和原始檔控制字元。 嚴格遵循原始檔控制外掛程式 API，可讓您輕鬆地整合到 Visual Studio，並為使用者提供無問題的體驗。 這表示原始檔控制外掛程式必須執行 API 中詳述的大部分函式和回呼。

 若要使用原始檔控制外掛程式 API 來執行原始檔控制外掛程式，請遵循下列步驟：

1. 建立 DLL，以執行[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)中指定的函式。

2. 藉由建立適當的登錄專案（如[如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)中所述）來註冊 DLL。

3. 建立 helper UI，並在原始檔控制介面卡套件出現提示時顯示（透過原始檔控制外掛程式處理原始檔控制功能的 Visual Studio 元件）

   為了回應原始檔控制命令，Visual Studio IDE 會針對基本作業呈現標準 UI，然後透過原始檔控制外掛程式 API 中定義的函式，將資訊傳遞至原始檔控制外掛程式。 針對 advanced 選項，可以在上呼叫原始檔控制外掛程式來呈現它自己的 UI，例如，流覽原始檔控制的專案。 這表示當處理原始檔控制時，使用者可能會看到兩個可能不同的 UI 樣式： Visual Studio 呈現的 UI，以及原始檔控制外掛程式所呈現的 UI。 這對先進的原始檔控制作業而言最為明顯。

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>執行原始檔控制外掛程式的缺點

- 針對先進的功能，使用者可能會看到兩種不同的介面樣式，因而導致可能的混淆。

- 原始檔控制外掛程式會局限于原始檔控制外掛程式 API 所隱含的原始檔控制模型。

- 原始檔控制外掛程式 API 對某些原始檔控制案例可能會有太大的限制。

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>執行原始檔控制外掛程式的優點

- Visual Studio 提供所有基本原始檔控制作業的所有 UI，讓原始檔控制外掛程式不必執行可能複雜的 UI。

- 由於是嚴格的 API，因此原始檔控制外掛程式可以輕鬆地與外部原始檔控制程式互動，以提供更廣泛的功能;Visual Studio 並不在意原始檔控制功能的完成方式，只會根據原始檔控制外掛程式 API 來完成。

- 執行原始檔控制外掛程式比原始檔控制 VSPackage 更容易。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 可透過完全控制原始檔控制功能來深入整合 Visual Studio，並完全取代 Visual Studio 提供的原始檔控制使用者介面。 原始檔控制 VSPackage 會向 Visual Studio 註冊，並提供原始檔控制功能。 雖然可以向 Visual Studio 註冊數個原始檔控制 Vspackage，但其中一次只能有一個作用中。 原始檔控制 VSPackage 可完整控制原始檔控制功能，以及在 Visual Studio 中的外觀。 可能在系統中註冊的其他所有原始檔控制 Vspackage 都處於非使用中狀態，而且完全不會顯示任何 UI。

 執行原始檔控制 VSPackage 需要「全有或無」策略。 原始檔控制 VSPackage 的建立者必須投入大量的時間來執行一些原始檔控制介面和新的 UI 元素（對話方塊、功能表和工具列），以涵蓋整個原始檔控制功能。 如需詳細資訊，請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) 。

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>執行原始檔控制 VSPackage 的缺點

- VSPackage 必須執行一些複雜介面，才能順利與 Visual Studio 整合。

- VSPackage 必須提供原始檔控制所需的所有 UI;Visual Studio 不會在此區域提供協助。

- 原始檔控制 VSPackage 會熟知系結至 Visual Studio，而且無法與獨立的程式一起運作，因此功能無法輕鬆地與原始檔控制程式的外部版本共用。

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>執行原始檔控制 VSPackage 的優點

- 因為 VSPackage 對原始檔控制 UI 和功能有完整的控制權，所以使用者會看到一個無縫介面來進行原始檔控制。

- VSPackage 不限於特定的原始檔控制模型。

## <a name="see-also"></a>請參閱
- [原始檔控制](../../extensibility/internals/source-control.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [原始檔控制的新功能](../../extensibility/internals/what-s-new-in-source-control.md)