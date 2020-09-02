---
title: Automation 模型總覽 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699520"
---
# <a name="automation-model-overview"></a>自動化模型概觀
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Automation 模型包含一組物件，可讓您撰寫 Visual Studio 的增益集或延伸模組。 增益集是一種應用程式，可操作 Visual Studio 環境並將一般工作自動化。 Visual Studio 擴充功能可以建立自訂 Visual Studio 元件，或新增至標準元件的功能，例如文字編輯器。  
  
## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件  
 Automation 模型包含可控制常見環境之主要 facet 的相關物件群組。 下列圖表顯示組成 automation 模型的大量物件集。  
  
 ![Visual Studio Automation 物件圖表](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio automation 物件  
  
 如需詳細資訊，請參閱 [擴充 Visual Studio 環境](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。  
  
 環境會針對不同的功能區域提供模型。 比方說，您可能會在程式碼中找到各種專案的程式碼模型。 有各種檔元素的檔模型。 VSPackage 提供者特別感興趣的一個區域（專案區域）。 您可能會想要讓新的專案類型能夠以 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 和參與 automation 模型的相同方式，來參與 automation 模型 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。 此程式會在為 [Vspackage 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)的過程中加以概述。  
  
 您可以考慮延伸環境自動化模型的位置：  
  
- 專案  
  
- Document  
  
- 程式碼  
  
- Build  
  
  如需自動化的詳細資訊，請參閱 [Visual Studio 的自動化和](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6)擴充性。 這份檔及其提供的連結，可協助您做出有關如何為 VSPackage 提供自動化的決策。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立增益集](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
