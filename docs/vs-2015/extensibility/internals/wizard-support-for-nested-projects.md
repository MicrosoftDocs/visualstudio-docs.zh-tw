---
title: 針對嵌套專案的 Wizard 支援 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 206fd12ea8f198e1659a49ed566e726e49878c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180344"
---
# <a name="wizard-support-for-nested-projects"></a>巢狀專案的精靈支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE 會執行兩個嚮導，讓嵌套專案的父專案可以執行： [ **新增專案** ] 和 [ **加入專案** ] wizard。  
  
 如果使用者在 [檔案] 功能表上選取 [**加入專案**]，然後按一下 [**新增**專案]，或在 [方案總管] 中選取 [**加入**] 和 [以滑鼠右鍵按一下**新專案**] 來啟動 [**新增**專案]，IDE 會執行**AddProject**命令，而**AddProject**命令的父專案執行會傳回範本專案檔，或包含一組內容參數的 wizard ( .vsz) 檔。  
  
 同樣地，父專案的 **AddItem** 嚮導的執行會傳回具有不同內容參數集的 .vsz 檔案。  
  
 如需有關嚮導的詳細資訊，請參閱 [Wizard (。.Vsz) ](../../extensibility/internals/wizard-dot-vsz-file.md)檔案、 [內容參數](../../extensibility/internals/context-parameters.md) ，以及 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)
