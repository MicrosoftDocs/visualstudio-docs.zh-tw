---
title: 為 Vspackage 提供自動化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d707c42196d727a35ca7c9d9cef250c60f7d5b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018068"
---
# <a name="providing-automation-for-vspackages"></a>為 VSPackage 提供自動化
有兩個主要的方式，可讓您的 Vspackage： 藉由實作 VSPackage 特有的物件，並藉由實作標準 automation 物件。 一般而言，這些一起用來擴充 automation 模型的環境。  
  
## <a name="vspackage-specific-objects"></a>VSPackage 特有的物件  
 Automation 模型內的特定位置會要求您提供特有 VSPackage 的 automation 物件。 比方說，新的專案需要不同只 VSPackage 提供的物件。 這些物件的名稱會在登錄中輸入，並透過呼叫環境取得`DTE`物件。  
  
 自動化取用者會使用透過標準的物件的物件屬性所提供的物件時，您也可以取得 VSPackage 特有的物件。 例如，標準`Window`物件具有`Object`屬性，通常稱為`Windows.Object`屬性。 當取用者呼叫`Window.Object`在視窗中，在 VSPackage 中實作，您將傳回您自己設計的特定的自動化物件。  
  
#### <a name="projects"></a>專案  
 Vspackage 可以擴充 automation 模型適用於透過自己的 VSPackage 特定物件的新專案類型。 VSPackage 要區分您唯一的專案，提供新的 automation 物件的主要目的的物件<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>或<xref:VSLangProj80.VSProject2>物件。 當您想要提供有辦法挑出或逐一查看您專案類型的其他專案類型，除了它們應該會出現並排顯示，此差異很方便在方案中。 如需詳細資訊，請參閱 <<c0> [ 公開專案物件](../../extensibility/internals/exposing-project-objects.md)。  
  
#### <a name="events"></a>事件  
 環境的事件架構提供讓您附加您自己的 VSPackage 特定物件的另一個位置。 例如，藉由建立您自己的獨特事件的物件，您可以擴充專案的環境的事件模型。 您可能想要提供您自己的新項目新增至您自己的專案類型時的事件。 如需詳細資訊，請參閱 <<c0> [ 公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。  
  
#### <a name="window-objects"></a>視窗物件  
 Windows 可以回 VSPackage 特定自動化將物件傳遞回呼叫時的環境。 實作物件衍生自<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，<xref:EnvDTE.IExtensibleObject>或`IDispatch`，傳遞回擴充中設置視窗物件的屬性。 例如，您可以使用這種方法可讓設置在視窗框架的控制項。 此物件及它可能會延長的任何其他物件的語意都是您要設計的。 如需詳細資訊，請參閱[＜How to：提供的 Windows 自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。  
  
#### <a name="options-pages-on-the-tools-menu"></a>在 [工具] 功能表上的 [選項] 頁面  
 您可以建立頁面，來擴充 工具、 選項 automation 模型，透過實作分頁，並將資訊新增至登錄，以建立您自己的選項。 然後可以透過環境物件模型，例如任何其他選項頁面呼叫頁面。 如果您要新增至 Vspackage 透過環境功能的設計需要選項 頁面，您應該新增的自動化支援。 如需詳細資訊，請參閱 <<c0> [ 選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)。  
  
## <a name="standard-automation-objects"></a>標準 Automation 物件  
 若要擴充的專案自動化，您也實作標準 automation 物件 (衍生自`IDispatch`)，就能除外的其他專案物件，並實作標準方法和屬性。 標準物件的範例包括專案的物件，例如插入解決方案階層`Projects`， `Project`， `ProjectItem`，和`ProjectItems`。 每個新的專案型別應該實作這些物件 （而且可能是語意根據您專案的其他項目）。  
  
 在某方面來說，這些物件會提供 VSPackage 特定專案物件的相對優點。 標準自動化物件可以讓您使用一般化的方式，例如支援相同物件的任何其他專案的專案。 因此，增益集撰寫針對一般`Project`和`ProjectItem`物件可以針對任何類型的專案運作。 如需詳細資訊，請參閱 <<c0> [ 專案模型化](../../extensibility/internals/project-modeling.md)。