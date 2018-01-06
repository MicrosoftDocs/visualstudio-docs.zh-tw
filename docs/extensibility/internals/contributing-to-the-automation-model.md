---
title: "參與 Automation 模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb69380913f188031c97b46530ea2659fc05fe30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-automation-model"></a>Contributing to the Automation Model
Visual Studio 會提供一組的 automation 介面的自訂環境。 Automation 模型是可讓使用者建立 Visual Studio 增益集和擴充功能的物件模型。  
  
 此外，也適用於您，身為 VSPackage 開發人員，參與 automation 模型;如此一來，您可以啟用 VSPackage 建立增益集，並使用您的 VSPackage 中時，通常提供模型一致性使用者經驗的使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 若要讓一般使用者經驗一致，您可遵循一組指導方針，讓 VSPackage 的 automation 模型會遵循概念，設計 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [Automation 模型概觀](../../extensibility/internals/automation-model-overview.md)  
 定義相關的群組控制一般環境的主要 facet 的物件的 automation 模型。 這組物件，如圖中的 automation 模型圖表所示。  
  
 [為 VSPackage 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)  
 討論可讓您的 VSPackage 的兩個主要方式。  
  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)  
 提供建立 VSPackage 特有之物件的逐步指示。  
  
 [將專案模型化](../../extensibility/internals/project-modeling.md)  
 說明建立新的專案類型的自動化所需的標準專案物件，並說明專案自動化遵循的路徑。 本主題也提供的宣告和實作類別的清單。  
  
 [公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 提供建立事件的 automation 模型的逐步指示。  
  
 [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)  
 描述如何傳回對 automation 物件支援的 VSPackage 屬性的自訂**選項** 對話方塊上的**工具**藉由擴充的功能表`DTE.Properties`物件。  
  
 [為程式碼提供自動化](../../extensibility/internals/providing-automation-for-code.md)  
 說明，建立 automation 模型，讓您的程式碼並不需要。 不過，本主題提供詳細的資訊儲存至程式碼模型提供的連結。  
  
 [如何︰為視窗提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 說明提供自動化是個好主意每當您想要的視窗中，使用 automation 物件和環境已不提供現成的自動化物件。 討論自動化的工具視窗與文件視窗。  
  
 [使用 Automation 模型](../../extensibility/internals/using-the-automation-model.md)  
 提供兩個程式碼範例顯示如何自動化取用者會取得初始專案 automation 物件。  
  
 [組態和 SelectedItem 物件的自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 提供有關組態選項的自動化和自動化的選取項目資訊。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 提供的程式碼範例示範如何 VSPackage 參與 DTE automation 物件模型。 列出參數、 傳回值，以及選取的 < 備註 >。  
  
## <a name="related-sections"></a>相關章節