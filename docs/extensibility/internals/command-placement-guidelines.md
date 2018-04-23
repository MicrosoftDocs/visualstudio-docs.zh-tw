---
title: 命令位置指導方針 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c406a5a34ea2556d367c8f7af8a9fda70fcc2676
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="command-placement-guidelines"></a>命令位置指導方針
在 Visual Studio 整合式的開發環境 (IDE) 中定位命令的最佳作法是根據命令集的大小而有所不同。 定義命令和定位根據.vsct 檔案中的資訊。  
  
## <a name="best-practices-for-all-command-sets"></a>所有的命令集的最佳作法  
 每一組命令，請遵循這些指導方針：  
  
-   事先準備命令結構的圖表。 識別命令、 下拉式方塊、 命令群組與用於多個位置的捷徑功能表。  
  
-   顯示在相同群組中的命令應該與相關。  
  
-   包含一個命令的群組是可接受的。  
  
-   封裝不應新增至現有的 Visual Studio 功能表的許多命令。 相反地，他們應該建立功能表或子功能表来裝載新的命令。  
  
-   當您將指令上現有的功能表，命令名稱，讓它的目的是清除並不會混淆與現有的命令。  
  
## <a name="best-practices-for-small-command-sets"></a>小型的命令集的最佳作法  
 如果您正在開發的 VSPackage，有幾個命令，也請遵循這些指導方針：  
  
-   可能的話，請使用[父項目](../../extensibility/parent-element.md)的命令、 下拉式方塊、 群組或子功能表將其置於適當的群組。  
  
-   這些群組指派至 VSPackage 所顯示的功能表。  
  
-   必須是父系的子功能表或命令[群組元素](../../extensibility/group-element.md)。 將命令和子功能表指派給群組，然後將群組指派給父功能表。  
  
-   您可以將命令放在其他群組加入[CommandPlacements 元素](../../extensibility/commandplacements-element.md)區段之後的命令定義，然後再將加入`CommandPlacements Element` [CommandPlacement 元素](../../extensibility/commandplacement-element.md)每個其他群組。  
  
## <a name="best-practices-for-large-command-sets"></a>較大的命令集的最佳作法  
 如果 VSPackage 會有許多命令將會出現在多個內容，也請遵循這些指導方針：  
  
-   請在功能表、 群組和自我的父代的命令。 也就是說，請勿指派`Parent Element`定義中的項目。  
  
-   使用`CommandPlacement Element`中的項目`CommandPlacements Element`區段，以將功能表、 群組和命令放在其父功能表和群組。  
  
-   在`CommandPlacements`區段中，填入指定的功能表項目或群組應在彼此相鄰。 這有助於提高可讀性，並使`Priority`排名更輕鬆地判斷。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)