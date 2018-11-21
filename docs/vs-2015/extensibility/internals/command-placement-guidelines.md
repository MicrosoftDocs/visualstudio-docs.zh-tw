---
title: 命令放置指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1729d4b5e65e60246926c1a3fd25342b10545068
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731001"
---
# <a name="command-placement-guidelines"></a>命令放置方針
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 整合式的開發環境 (IDE) 中的定位命令的最佳作法是根據命令集的大小而有所不同。 命令所定義，且位於根據.vsct 檔案中的資訊。  
  
## <a name="best-practices-for-all-command-sets"></a>所有的命令集的最佳作法  
 每一組命令，請遵循這些指導方針：  
  
-   事先準備命令結構的圖表。 識別命令、 下拉式方塊、 命令群組與將用於多個位置的捷徑功能表。  
  
-   出現在相同群組中的命令應該與相關。  
  
-   群組包含一個命令可接受的。  
  
-   封裝應該新增至現有的 Visual Studio 功能表的許多命令。 相反地，它們應該建立功能表或子功能表，來裝載新的命令。  
  
-   當您暫停命令現有的功能表名稱的命令，讓它的目的是清除並不會混淆與現有的命令。  
  
## <a name="best-practices-for-small-command-sets"></a>小型的命令集的最佳作法  
 如果您正在開發的 VSPackage，有少數的命令，也請遵循這些指導方針：  
  
-   可能的話，請使用[父元素](../../extensibility/parent-element.md)的命令、 下拉式方塊、 群組或子功能表將它放在適當的群組。  
  
-   將這些群組指派至 VSPackage 所顯示的功能表。  
  
-   必須是父系的子功能表或命令[群組項目](../../extensibility/group-element.md)。 將命令和子功能表指派給群組，然後將群組指派給父功能表。  
  
-   您可以將命令放在其他群組加[CommandPlacements 元素](../../extensibility/commandplacements-element.md)區段的命令中，定義之後，然後再將加入`CommandPlacements Element` [CommandPlacement 元素](../../extensibility/commandplacement-element.md)每個其他群組。  
  
## <a name="best-practices-for-large-command-sets"></a>大型的命令集的最佳作法  
 如果 VSPackage 必須將出現在多個內容中的許多命令，也請遵循這些指導方針：  
  
-   請功能表、 群組和自我的父代的命令。 也就是說，不要指派`Parent Element`定義中的項目。  
  
-   使用`CommandPlacement Element`中的項目`CommandPlacements Element`一節，以將功能表、 群組和命令放在其父功能表和群組。  
  
-   在 `CommandPlacements`區段中，填入指定的功能表項目或群組應彼此相鄰。 這有助於提高可讀性，並使`Priority`更輕鬆地判斷的排名。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

