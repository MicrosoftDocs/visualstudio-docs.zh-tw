---
title: 提供 Vspackage 的自動化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="providing-automation-for-vspackages"></a>提供 Vspackage 的自動化
有兩種主要方式可讓您的 Vspackage： 藉由實作 VSPackage 特定物件，並藉由實作標準 automation 物件。 一般而言，這些項目用於一起擴充 automation 模型的環境。  
  
## <a name="vspackage-specific-objects"></a>VSPackage 特定物件  
 Automation 模型內的特定位置會要求您提供 VSPackage 獨有的 automation 物件。 比方說，新的專案需要您的 VSPackage 提供的不同物件。 這些物件的名稱在登錄中輸入並取得透過呼叫環境`DTE`物件。  
  
 自動化取用者會使用透過標準物件的物件屬性所提供的物件時，您也可以取得 VSPackage 特有物件。 例如，標準`Window`物件具有`Object`屬性，通常稱為`Windows.Object`屬性。 當取用者呼叫`Window.Object`在 VSPackage 中實作的視窗，您將傳遞回您專屬設計的特定自動化物件。  
  
#### <a name="projects"></a>專案  
 Vspackage 可以擴充 automation 模型，適用於新的專案類型，透過其自己的 VSPackage 特定物件。 從物件提供新的 automation 物件，來區分您唯一的專案您的 VSPackage 的主要目的<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>或<xref:VSLangProj80.VSProject2>物件。 此差異很方便，當您想要提供挑出或逐一查看您的專案，除了其他專案類型，類型的方法應該顯示由並行的方案中。 如需詳細資訊，請參閱[公開專案物件](../../extensibility/internals/exposing-project-objects.md)。  
  
#### <a name="events"></a>事件  
 事件架構的環境中提供另一個位置，以新增您自己的 VSPackage 特定物件。 例如，藉由建立您自己的唯一事件物件，您可以擴充專案的環境的事件模型。 您可能想要提供您自己的事件，當新項目加入您自己的專案類型。 如需詳細資訊，請參閱[公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。  
  
#### <a name="window-objects"></a>視窗物件  
 Windows 可以傳遞回 VSPackage 特定自動化物件至環境時呼叫。 實作衍生自物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，<xref:EnvDTE.IExtensibleObject>或`IDispatch`，交回延伸已決定位置所在的視窗物件的屬性。 例如，您可以使用這種方法可讓位於視窗框架的控制項。 此物件和任何其他物件，它可能會延長語意為您設計。 如需詳細資訊，請參閱[如何： 為 Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。  
  
#### <a name="options-pages-on-the-tools-menu"></a>在 [工具] 功能表上的 [選項] 頁面  
 您可以建立頁面，以擴充工具，選項 automation 模型，透過實作網頁並將資訊新增至登錄以建立您自己的選項。 透過環境物件模型，像任何其他選項 頁面便可以呼叫您的網頁。 如果您要加入至 VSPackages 透過環境功能的設計需要選項 頁面，您應該加入的自動化支援。 如需詳細資訊，請參閱[選項頁面的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)。  
  
## <a name="standard-automation-objects"></a>標準 Automation 物件  
 若要擴充的專案自動化，您也實作標準 automation 物件 (衍生自`IDispatch`) 獨立除外的其他專案物件，而且實作標準的方法和屬性。 標準物件的範例包括例如會插入至方案階層架構的專案物件`Projects`， `Project`， `ProjectItem`，和`ProjectItems`。 每個新的專案類型應該實作這些物件 （而且可能是語意根據專案的其他項目）。  
  
 某方面來說，這些物件會提供 VSPackage 特定專案中物件的相反的優點。 所有標準 automation 物件可讓您可以像是其他任何專案支援相同物件的通用方式使用的專案。 因此，增益集撰寫針對一般`Project`和`ProjectItem`物件可以根據任何類型的專案運作。 如需詳細資訊，請參閱[專案模型](../../extensibility/internals/project-modeling.md)。