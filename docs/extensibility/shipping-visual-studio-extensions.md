---
title: "傳送 Visual Studio 擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 543f107081a5cc29ac14f1c2ba2e05924b72e353
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="shipping-visual-studio-extensions"></a>傳送 Visual Studio 擴充功能
您完成開發您的擴充功能之後，您可以將它安裝在其他電腦上、 共用與朋友或同事，或發行 Visual Studio Marketplace 上。 本節中，我們說明您需要執行動作以發行和維護您的擴充功能的所有事情：.vsix 檔案時，發佈、 當地語系化，以及更新工作。  
  
## <a name="working-with-vsix-extensions"></a>使用 VSIX 擴充功能  
 您可以建立空白的 VSIX 專案，並再加入另一個項目範本，以建立 VSIX 擴充功能。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
 您可以使用 VSIX 格式封裝專案範本、 項目範本，Vspackage，Managed Extensibility Framework (MEF) 元件，以**工具箱**控制項、 組件和自訂型別 （這包括自訂起始頁）。 VSIX 格式使用以檔案為基礎的部署。 如需 VSIX 套件的詳細資訊，請參閱[VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)。  
  
 VSIX 格式不支援安裝的程式碼片段。 它也不支援某些其他功能，例如寫入至全域組件快取 (GAC) 或系統登錄。 如果您需要寫入至 GAC 中，或是在安裝中的登錄，您必須使用 Windows Installer。 如需詳細資訊，請參閱[準備擴充功能的 Windows Installer 部署](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace 中發佈您的擴充功能  
 您可以擴充散佈給其他人只要郵寄它們.vsix 檔，或放在伺服器上。 但若要取得您的程式碼的許多人，最好是將它放在[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 Visual Studio Marketplace 延伸模組都可透過 Visual Studio 使用者**擴充功能和更新**。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。  
  
 如需示範如何將擴充功能上傳至 Visual Studio Marketplace 的完整範例，請參閱[逐步解說： 發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。  
  
## <a name="private-galleries"></a>Private Galleries  
 當您開發的控制項、 範本和工具，則您可以張貼到內部網路上的私用組件庫與組織共用它們。 如需詳細資訊，請參閱[私用組件庫](../extensibility/private-galleries.md)。  
  
## <a name="localizing-your-extension"></a>當地語系化您的擴充功能  
 如果您計劃要發行您的擴充功能在不同的地區設定中，您應該考慮將它當地語系化。 如需相關資訊的說明，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="updating-and-versioning-your-extension"></a>更新和版本控制您的擴充功能  
 您已發行您的擴充功能之後，會出現一次當您需要更新應用程式。 若要了解如何更新已在 Visual Studio Marketplace 發行的擴充功能，請參閱[How to： 更新擴充功能](../extensibility/how-to-update-a-visual-studio-extension.md)。  
  
 您可以設定您的擴充功能以支援多個版本的 Visual Studio。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)|說明如何使用 VSIX 專案範本來安裝自訂專案範本。|  
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 套件的元件。|  
|[VSIX 專案範本](../extensibility/vsix-project-template.md)|提供有關如何封裝及發行擴充功能的逐步指示。|  
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|說明如何使用 extension.vsixlangpack 檔案安裝程序提供當地語系化的文字。|  
|[如何： 更新擴充功能](../extensibility/how-to-update-a-visual-studio-extension.md)|描述如何更新您的系統上的擴充，以及如何將更新部署至現有的 Visual Studio 擴充功能。|  
|[如何︰將相依性加入至 VSIX 封裝](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|描述如何將參考加入至 VSIX 部署封裝。|  
|[準備適用於 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|說明如何將延伸模組使用 Windows Installer 部署。|  
|[簽署 VSIX 封裝](../extensibility/signing-vsix-packages.md)|說明如何簽署 VSIX 封裝。|  
|[私用組件庫](../extensibility/private-galleries.md)|說明如何建立擴充功能私用組件庫。|  
|[支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)|示範如何延伸模組支援多個版本的 Visual Studio。|
|[尋找 Visual Studio](locating-visual-studio.md)|說明如何找到自訂延伸模組部署 Visual Studio 執行個體。|
