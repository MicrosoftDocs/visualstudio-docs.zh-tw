---
title: Automation 模型概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9369bb6074bb294223051ba7dfa158648fe0cad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="automation-model-overview"></a>Automation 模型概觀
Automation 模型包含一組針對，您可以撰寫 Visual Studio 增益集或擴充功能的物件。 增益集是應用程式可以操作 Visual Studio 環境並自動化一般工作。 Visual Studio 擴充功能可以建立自訂 Visual Studio 元件，或加入至標準元件，例如文字編輯器功能。  
  
## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件  
 Automation 模型相關的控制一般環境的主要 facet 的物件群組所組成。 以下是此圖顯示一組更周延的撰寫 automation 模型的物件。  
  
 ![Visual Studio Automation 物件圖表](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio automation 物件  
  
 如需詳細資訊，請參閱[擴充 Visual Studio 環境](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 環境提供不同功能區域的模型。 例如，為各種項目，您可能會在程式碼中發現的程式碼模型。 沒有文件模型的各種文件項目。 一個區域中，專案區域中，是 VSPackage 提供者特別感興趣。 您可能會想要參與 automation 模型中的相同方式進行做為您新專案類型[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]參與 automation 模型。 處理序述[提供 Vspackage 的自動化](../../extensibility/internals/providing-automation-for-vspackages.md)。  
  
 位置，考慮擴充 automation 模型的環境：  
  
-   專案  
  
-   文件  
  
-   程式碼  
  
-   組建  
  
 如需有關自動化的詳細資訊，請參閱[自動化和擴充性 Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)。 這份文件，而且文件提供的連結，幫助您做出有關應如何提供 VSPackage 的自動化。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立增益集](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)