---
title: 加入專案和專案專案範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203867"
---
# <a name="adding-project-and-project-item-templates"></a>新增專案與專案項目範本
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您建立自己的專案類型時，您必須使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (IDE) 對話方塊的標準整合式開發環境，以提供新增專案和專案專案的支援。 下列主題討論新增專案和專案專案的不同技術。  
  
## <a name="in-this-section"></a>本節內容  
 [專案內容](../../extensibility/internals/project-context.md)  
 說明專案會提供環境中過大幅簡化的大部分內容資訊。  
  
 [專案優先順序](../../extensibility/internals/project-priority.md)  
 說明專案專案通常是一個專案的成員，以避免對用來開啟專案的專案有混淆。  
  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)  
 提供兩種編輯器類型的相關資訊，這些編輯器可用來開啟專案中的檔案，以及專案在判斷專案專案開啟時所要使用的編輯器中所扮演的角色。  
  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)  
 說明建立專案時所發生的情況 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [將項目新增至新增項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 說明在 [ **加入新專案** ] 對話方塊中加入專案的流程。  
  
 [將目錄新增至新增專案對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 提供註冊新目錄的範例，其中包含 VSPackage 所提供的自訂範本。  
  
 [將目錄新增至新增項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 提供針對 [ **加入新專案** ] 對話方塊註冊一組新目錄的範例。  
  
 [用來擴充專案系統的 IDE 定義的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 列出用來擴充專案系統的不同命令專案類型。  
  
 [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 列出用來擴充 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 、 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 和專案系統的物件 catid [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。  
  
## <a name="related-sections"></a>相關章節  
 [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供逐步指示，說明如何開啟專案的本質系結至特定編輯器。  
  
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)  
 提供開啟標準編輯器的逐步指示。  
  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 提供專案子類型概念主題的連結。 專案子類型會擴充現有 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 的和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供其他主題的連結，這些主題提供如何設計新專案類型的相關資訊。
