---
title: 原始檔控制整合概觀 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4bd2a688e2a10bf0b931851b0d4366684820bf1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049915"
---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節將比較兩種方式，將整合到 Visual Studio 原始檔控制原始檔控制外掛程式和 VSPackage 所提供的原始檔控制解決方案，並反白顯示新的原始檔控制功能。 Visual Studio 可讓手動切換原始檔控制 Vspackage 和原始檔控制外掛程式，以及自動以解決方案為基礎的切換。

## <a name="source-control-integration"></a>原始檔控制整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合選項。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您仍舊可以根據原始檔控制外掛程式 API （先前也稱為 MSSCCI API），可提供基本的原始檔控制功能時使用 Visual Studio 原始檔控制使用者介面 （外掛程式UI)。 原始檔控制 VSPackage，相反地，提供新的深度整合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適用於需要高層級的複雜度，以及在原始檔控制模型中的自我管理的原始檔控制整合的路徑。

 ![原始檔控制概觀](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 所有版本的 Visual Studio 都支援整合路徑的原始檔控制外掛程式 API 規格 1.2 版。 原始檔控制外掛程式實作寫入實作原始檔控制整合和註冊的原始檔控制外掛程式 API 函式中所述的 DLL[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。 這種方法，使用整合式開發環境 (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI 對話方塊，例如簽入、 簽出、 工具/選項屬性頁、 工具列和原始檔控制圖像 （glyph）。 嚴格遵循原始檔控制外掛程式 API，可確保 Visual Studio 和使用者的麻煩體驗進行整合。 這表示原始檔控制外掛程式必須實作的大部分函式和詳細的 API 中的回呼。

 若要實作原始檔控制外掛程式使用原始檔控制外掛程式 API，請遵循下列步驟：

1. 建立一個實作中指定的函式的 DLL[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。

2. 藉由適當的登錄項目註冊的 DLL (中所述[How to:安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。

3. UI 和顯示原始檔控制配接器套件 （會處理透過原始檔控制外掛程式的原始檔控制功能的 Visual Studio 元件） 出現提示時，建立協助程式

   在原始檔控制命令的回應，Visual Studio IDE 提供的基本作業的標準 UI，然後將資訊傳遞至原始檔控制外掛程式透過原始檔控制外掛程式 API 中所定義的函式。 如需進階的選項，原始檔控制外掛程式上無法呼叫來呈現它自己的 UI，比方說，瀏覽原始檔控制專案。 這表示，使用者可能會顯示兩個可能是不同的 UI 處理原始檔控制時： Visual Studio 會顯示 UI 和原始檔控制外掛程式所提供的 UI。 這是最明顯與進階的原始檔控制作業。

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>若要實作原始檔控制外掛程式的缺點

- 如需進階的功能，使用者可能會看到兩個不同的樣式的介面，導致混淆。

- 原始檔控制外掛程式會侷限於原始檔控制外掛程式 API 所隱含的原始檔控制模型。

- 原始檔控制外掛程式 API 可能會太嚴格，某些原始檔控制的案例。

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>若要實作原始檔控制外掛程式的優點

- Visual Studio 會提供所有基本的原始檔控制作業的所有 UI，讓原始檔控制外掛程式不需要實作可能很複雜的 UI。

- 因為嚴格的 API，而原始檔控制外掛程式可以輕易地與外部來源控制程式互動以提供更廣泛的功能;Visual Studio 不在意太遠如何原始檔控制功能完成此動作，只根據原始檔控制外掛程式 API 來完成。

- 很容易實作的原始檔控制外掛程式比原始檔控制 VSPackage。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 用來與原始檔控制功能的完整控制權和完全取代 Visual Studio 提供的原始檔控制使用者介面的 Visual Studio 的深度整合。 原始檔控制 VSPackage 註冊使用 Visual Studio，並提供原始檔控制功能。 雖然可以使用 Visual Studio 註冊數個原始檔控制 Vspackage，其中只有一個可以作用一次。 原始檔控制 VSPackage 有 Visual Studio 中的原始檔控制功能和外觀的完整控制權，在作用中狀態。 所有其他原始檔控制 Vspackage 可能會在系統中註冊之非使用中且不會完全顯示任何 UI。

 實作原始檔控制 VSPackage，需要 「 全部或全無 」 的策略。 原始檔控制 VSPackage 的建立者必須投入大量心力來實作原始檔控制的介面和新的 UI 項目 （對話方塊、 功能表和工具列） 以涵蓋整個來源控制項功能的數字。 請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)如需詳細資訊。

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>若要實作原始檔控制 VSPackage 的缺點

- VSPackage 必須實作許多複雜的介面，以便與 Visual Studio 成功整合。

- VSPackage 必須提供所需的原始檔控制的所有 UIVisual Studio 會提供任何這方面的協助。

- 原始檔控制 VSPackage 會緊密繫結至 Visual Studio，並與原始檔控制程式的外部版本無法輕易共用功能，因此無法使用獨立程式。

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>若要實作原始檔控制 VSPackage 的優點

- VSPackage 的原始檔控制 UI 的完整控制權和功能，因為使用者會看到原始檔控制的無縫式介面。

- VSPackage 不會侷限於特定的來源控制模型中。

## <a name="see-also"></a>另請參閱
- [原始檔控制](../../extensibility/internals/source-control.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [原始檔控制的新功能](../../extensibility/internals/what-s-new-in-source-control.md)