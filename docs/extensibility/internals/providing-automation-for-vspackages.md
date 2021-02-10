---
title: 為 Vspackage 提供自動化 |Microsoft Docs
description: 瞭解如何藉由執行 VSPackage 專屬的物件和執行標準 automation 物件，為您的 Vspackage 提供自動化功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d5a0bd912dadf6b8f90aabd846c6ac44534c917
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934073"
---
# <a name="providing-automation-for-vspackages"></a>為 VSPackage 提供自動化
有兩種主要的方式可為您的 Vspackage 提供自動化：藉由執行 VSPackage 專屬的物件和執行標準 automation 物件。 一般而言，這些會一起用來擴充環境的自動化模型。

## <a name="vspackage-specific-objects"></a>VSPackage-Specific 物件
 Automation 模型內的特定位置需要您提供 VSPackage 專屬的自動化物件。 比方說，新的專案需要只有您的 VSPackage 提供的不同物件。 這些物件的名稱會在登錄中輸入，並透過呼叫環境物件來取得 `DTE` 。

 當自動化取用者使用透過標準物件的 Object 屬性提供的物件時，也可以取得 VSPackage 特定的物件。 例如，標準 `Window` 物件有一個 `Object` 屬性，通常稱為屬性（property） `Windows.Object` 。 當取用者在 `Window.Object` VSPackage 中執行的視窗上呼叫時，您會傳回您自己設計的特定 automation 物件。

#### <a name="projects"></a>專案
 Vspackage 可以透過自己的 VSPackage 專屬物件，為新的專案類型延伸 automation 模型。 為您的 VSPackage 提供新 automation 物件的主要目的是要區分您的唯一專案物件與 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> 或 <xref:VSLangProj80.VSProject2> 物件。 當您想要提供一種方式，讓您的專案與其他專案類型分開或逐一查看專案類型時，這項差異很方便，因為它們會在解決方案中並存顯示。 如需詳細資訊，請參閱 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)。

#### <a name="events"></a>事件
 環境的事件架構會提供另一個位置，供您附加自己的 VSPackage 專屬物件。 例如，藉由建立您自己的唯一事件物件，您可以擴充專案的環境事件模型。 當新專案新增至您自己的專案類型時，您可能會想要提供自己的事件。 如需詳細資訊，請參閱 [公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。

#### <a name="window-objects"></a>視窗物件
 Windows 可以在呼叫時將 VSPackage 特定的 automation 物件傳回給環境。 您可以執行衍生自的物件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> ， <xref:EnvDTE.IExtensibleObject> 或將 `IDispatch` 屬性（property）擴充到其所在的視窗物件。 例如，您可以使用這個方法，為視窗框架中的控制項提供自動化功能。 此物件的語法及其可能擴充的任何其他物件，都是您要設計的。 如需詳細資訊，請參閱 [如何：為 Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。

#### <a name="options-pages-on-the-tools-menu"></a>[工具] 功能表上的 [選項] 頁面
 您可以建立頁面來擴充工具、透過執行頁面的選項自動化模型，以及將資訊新增至登錄，以建立您自己的選項。 然後您可以透過環境物件模型來呼叫您的頁面，就像任何其他選項頁面一樣。 如果您要透過 Vspackage 新增至環境的功能設計需要 [選項] 頁面，則您也應該新增自動化支援。 如需詳細資訊，請參閱 [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)。

## <a name="standard-automation-objects"></a>標準 Automation 物件
 若要擴充專案的自動化，您也可以執行標準 automation 物件， (衍生自 `IDispatch` 其他專案物件以外的) ，並執行標準方法和屬性。 標準物件的範例包括插入至方案階層的專案物件，例如 `Projects` 、 `Project` 、 `ProjectItem` 和 `ProjectItems` 。 每個新的專案類型都應該根據您專案的)  (，來執行這些物件，也可能是其他物件。

 就某個方面來說，這些物件會提供 VSPackage 特定專案物件的相反優點。 標準 automation 物件可讓您以一般化的方式使用您的專案，就像任何其他支援相同物件的專案一樣。 因此，針對一般和物件撰寫的增益集 `Project` `ProjectItem` 可以針對任何類型的專案運作。 如需詳細資訊，請參閱 [專案模型](../../extensibility/internals/project-modeling.md)化。
