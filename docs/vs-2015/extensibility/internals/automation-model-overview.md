---
title: Automation 模型概觀 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699520"
---
# <a name="automation-model-overview"></a>自動化模型概觀
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Automation 模型包含一組您可以對其撰寫的 Visual Studio 增益集或延伸的物件。 增益集是應用程式可以在 Visual Studio 環境的操作和自動化一般工作。 Visual Studio 擴充功能可以建立自訂的 Visual Studio 元件，或新增功能的標準元件，例如文字編輯器。  
  
## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件  
 Automation 模型相關的控制項通用的環境的主要層面的物件群組所組成。 以下是此圖顯示一組廣泛的撰寫自動化模型的物件。  
  
 ![Visual Studio Automation 物件圖表](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio automation 物件  
  
 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 環境](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 環境會提供不同功能區域中的模型。 比方說，是程式碼模型的各種您可能會發現程式碼中的項目。 沒有文件模型的各種文件項目。 一個區域中，[專案] 區域中，是 VSPackage 提供者的特別感興趣。 您可能會想要參與 automation 模型中相同的方式為您新的專案類型[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]和[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]參與 automation 模型。 處理程序中所述[Vspackage 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)。  
  
 其中您可以考慮擴充 automation 模型之環境的位置：  
  
- 專案  
  
- 文件  
  
- 程式碼  
  
- 組建  
  
  如需有關自動化的詳細資訊，請參閱[Automation 和擴充性 Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6)。 這份文件和文件它會提供連結，幫助您做出有關您應該提供 vspackage 的自動化的方式。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立增益集](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
