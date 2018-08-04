---
title: 參與 Automation 模型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d56b446914ae7345ccb0d393db8f17fc7f82c47
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513181"
---
# <a name="contribute-to-the-automation-model"></a>參與 automation 模型
Visual Studio 會提供一組自動化介面的自訂環境。 Automation 模型是可讓使用者建立 Visual Studio 增益集和擴充功能的物件模型。  
  
 此外，它是適用於您，身為 VSPackage 開發人員，參與 automation 模型;如此一來，您可以讓 VSPackage 建立增益集，並在使用您的 VSPackage 中時，通常提供模型一致的使用者經驗的使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 若要讓終端使用者體驗一致，您可以遵循一組指導方針，讓 VSPackage 的 automation 模型會遵循在概念設計 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [Automation 模型概觀](../../extensibility/internals/automation-model-overview.md)  
 Automation 模型定義相關的控制項通用的環境的主要層面的物件群組。 這組物件，如圖中的 automation 模型圖表所示。  
  
 [提供適用於 Vspackage 的自動化](../../extensibility/internals/providing-automation-for-vspackages.md)  
 討論可讓 VSPackage 的兩個主要方式。  
  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)  
 提供建立 VSPackage 特定物件的逐步指示。  
  
 [專案模型化](../../extensibility/internals/project-modeling.md)  
 說明建立新的專案類型的自動化所需的標準專案物件，並說明專案自動化遵循的路徑。 本主題也提供的宣告和實作適用於類別的清單。  
  
 [公開 （expose) 事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 提供逐步指示來建立您的自動化模型的事件。  
  
 [自動化支援的選項頁面](../../extensibility/internals/automation-support-for-options-pages.md)  
 描述如何傳回的 automation 物件支援的 VSPackage 屬性的自訂**選項** 對話方塊中於**工具**藉由擴充的功能表`DTE.Properties`物件。  
  
 [提供自動化的程式碼](../../extensibility/internals/providing-automation-for-code.md)  
 說明，建立的自動化模型，讓您的程式碼並不需要。 不過，就會提供具洞察力的資訊，程式碼模型到本主題中提供的連結。  
  
 [如何： 提供的 Windows 自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 說明提供自動化是個不錯的主意每當您想要在視窗中，提供 automation 物件和環境已不提供現成的自動化物件。 討論自動化工具視窗和文件視窗。  
  
 [使用 automation 模型](../../extensibility/internals/using-the-automation-model.md)  
 提供兩個程式碼範例示範如何自動化取用者會取得初始專案 automation 物件。  
  
 [組態和 SelectedItem 物件的自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 提供自動化組態與 SelectedItems 物件的相關資訊。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 提供 VSPackage 如何參與 DTE 自動化物件模型會顯示的程式碼範例。 列出參數、 傳回值，以及所選的 < 備註 >。  
  
