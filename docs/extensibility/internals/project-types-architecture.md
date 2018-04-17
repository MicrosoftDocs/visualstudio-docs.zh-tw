---
title: 專案型別架構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 6
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 34402ae0b998d4ae534507e23ffa31e0d7cef9bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="project-types-architecture"></a>專案類型的架構
本節包含有關架構中的專案類型的詳細的資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)  
 列出專案類型可以取用的服務，它必須實作的介面。  
  
 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)  
 描述專案類型都必須實作和 （選擇性） 可實作以提供其他功能的介面。  
  
 [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)  
 可以協助您決定當您必須建立一個專案類型和時，您可以使用另一個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]例如 Vspackage 和編輯器達成相同的擴充功能。  
  
 [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)  
 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會使用階層和選取範圍內容提供一致且簡化使用者經驗。  
  
## <a name="related-sections"></a>相關章節  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 說明如何專案子類型可讓您自訂的專案系統的行為[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供的專案概觀，做為基本建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 說明如何專案控制建立和編譯程式碼的其他主題會提供連結。